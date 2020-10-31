# Backup and restore for Gitea in Docker
You can use these scripts to create a backup of your Gitea, and restore it later. I use MariaDB.
MariaDB and Gitea are both in seperate docker-compose files

### Dependencies
- unzip
- rsync

### Backup
You'll have to change this to match your setup.
```
#!/bin/bash
/usr/bin/docker exec -u git -t -w /backup $(docker ps -qf "label=traefik.http.routers.gitea-web.rule=Host(\`gitea.apps.thedutchmc.nl\`)") bash -c '/app/gitea/gitea dump -c /data/gitea/conf/app.ini'
```

### Restore
You'll have to change this to match your setup. You should only need to change the variables.
```
#!/bin/bash

#Check if the user gave us the zip file they want to restore or not
if [[ $# -eq 0 ]]
then
        echo "You need to give us the ZIP file you want to restore"
        exit 1
fi

#System variables
TMP_DIR=/tmp
GITEA_ZIP=$1
GITEA_DUMP=$TMP_DIR/$(basename $GITEA_ZIP)

#User variables
GITEA_COMPOSE=PATH TO GITEA DOCKER COMPOSE
MARIADB_COMPOSE=PATH TO MARIADB COMPOSE
GIT_VOLUME=PATH TO GITEA GIT FOLDER
GITEA_VOLUME=PATH TO GITEA GITEA FOLDER
DB_CONTAINERNAME=MARIADB CONTAINER NAME
DB_NAME=GITEA DB
DB_ROOT_USERNAME=DB ROOT USER
DB_ROOT_PASSW=DB ROOT PASSWORD
DB_GITEA_USERNAME=GITEA DB USER
GITEA_USER_ID=GITEA USER ID

docker-compose -f $GITEA_COMPOSE down

echo "Cleaning Gitea Git folder"
rm -rf $GIT_VOLUME

echo "Unpacking $GITEA_ZIP to $TMP_DIR"
unzip -q -u $GITEA_ZIP -d $GITEA_DUMP -x log/* app.ini

mkdir -p $GITEA_VOLUME $GIT_VOLUME

echo "Copying config dump into $GITEA_VOLUME"
rsync -ah $GITEA_DUMP/data $GITEA_VOLUME/ --exclude gitea-*

echo "Moving Git repositories into $GIT_VOLUME"
rsync -ah $GITEA_DUMP/repos/* $GIT_VOLUME/repositories

echo "Applying permissions"
chown -R $GITEA_USER_ID:$GITEA_USER_ID $GIT_VOLUME $GITEA_VOLUME
chmod -R g+rw $GIT_VOLUME $GITEA_VOLUME

echo "Cleaning database"
docker-compose -f $MARIADB_COMPOSE exec $DB_CONTAINERNAME mysql -u $DB_ROOT_USERNAME -p$DB_ROOT_PASSW -e 'DROP DATABASE '"${DB_NAME}"';'

echo "Creating new database"
docker-compose -f $MARIADB_COMPOSE exec $DB_CONTAINERNAME mysql -u $DB_ROOT_USERNAME -p$DB_ROOT_PASSW -e 'CREATE DATABASE '"${DB_NAME}"';'
docker-compose -f $MARIADB_COMPOSE exec $DB_CONTAINERNAME mysql -u $DB_ROOT_USERNAME -p$DB_ROOT_PASSW -e 'GRANT ALL PRIVILEGES ON '"${DB_NAME}"'.* TO '"'${DB_GITEA_USERNAME}'"'@'"'%'"';'

echo "Restoring database"
cat $GITEA_DUMP/gitea-db.sql | docker exec -i $DB_CONTAINERNAME mysql -u $DB_ROOT_USERNAME -p$DB_ROOT_PASSW $DB_NAME

echo "Restoring complete. Starting Gitea"
docker-compose -f $GITEA_COMPOSE up -d

echo "Cleaning up"
rm -rf $GITEA_DUMP

echo "Check the logs for any errors:"
echo "tail -F $GITEA_VOLUME/log/gitea.log"

echo "Done."
```