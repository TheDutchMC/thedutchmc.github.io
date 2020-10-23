# Installation
[Back to libAuthDiscord](/wiki/plugins/libAuthDiscord/index.md)


1) Enable Developer mode on discord

> **Note:** Discord has a guide on this [here](https://support.discord.com/hc/en-us/articles/206346498-Where-can-I-find-my-User-Server-Message-ID-)

2) Create a Bot [here](https://discord.com/developers) and invite the bot to your server.

> **Note:** DiscordPy has a guide on this [here](https://discordpy.readthedocs.io/en/latest/discord.html)

3) Copy the bot token (found under the `Bot` section of your Bot application) into the config.yml of LibAuthDiscord
4) Right click your server icon in discord and select `copy id`, this is your guild ID, and paste this into the config.yml too.
5) To get a role ID, assign the role to a user, click their name and then right click on the role and select `copy ID`. In the config it should be set as follows:
```
permittedRoles:
- <role id 1>
- <role id 2>
- ...
```

> **Note:** Do not include the ``<`` and ``>`` symbols. Also make sure there is a space between the role ID and the hyphen symbol (``-``)