# Commands
[Back to uhcplus](/wiki/plugins/uhcplus/index.md)

The base command for UHcPlus is /uhcp, most of the commands will start with this.

- /uhcp start: This will start the UHC.
- /uhcp help: This will show you the help page.
- /uhcp version: This will show you the version of UhcPlus you are using.
- /uhcp teams: Teams base command.
    - /uhcp teams getteams: This will show you all the teams and how many players are in each team
    - /uhcp teams help: This will show you the help page for the Teams commands.
    - /uhcp teams jointeam <team id>: This will join you in to the provided Team.
    - /uhcp teams randomfill: This will randomly resort all the teams.
    - /uhcp teams teamcount: This will show you how many teams there can be with the current configuration.
    - /uhcp teams whichteam <player name>: This will show you in which team the provided player is.
- /uhcp preset: Preset base command
    - /uhcp preset create <name>: This will create a preset with the given name.
    - /uhcp preset delete <name>: This will delete the preset with the given name.
    - /uhcp preset help: This will show you the Preset command help page.
    - /uhcp preset list: This will list all available Presets.
    - /uhcp preset load <name>: This will load the preset with the given name.
    - /uhcp preset seeloaded: This will show you which preset is currently loaded.
    - /uhcp preset setdefaul <name>: This will set the default preset loaded when the server starts
    - /uhcp preset options: Preset Options base command.
        - /uhcp preset options list [page]: This will show what options you can modify.
        - /uhcp preset options <option> <value>: This will change the given option to the given value. It will change it on the currently loaded preset!
- /broadcast: This will broadcast a message to all players.
- /c and /coords: This will put the player's coordinates in Team chat if enabled.
- /ti and /teaminventory: This will open the Team Inventory, if enabled/
- /chat: This will switch your chat between global and team chat