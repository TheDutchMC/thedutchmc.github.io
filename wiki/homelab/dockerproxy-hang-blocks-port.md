# Docker-Proxy hangs and blocks ports
Today I ran into an issue where Docker went on a rampage, including the docker-proxy. With all containers stopped and docker restarted, 
docker-proxy would remain after restarting Docker, and block ports. This prevents the containers from restarting.

### Environment
OS: Ubuntu 18.04 LTS
Docker version: 19.03.11, build 42e35e61f3

### Solution
1. ``sudo systemctl stop docker``
2. ``sudo rm -f /var/lib/docker/network/files-kv.db``
3. ``sudo systemctl start docker``
