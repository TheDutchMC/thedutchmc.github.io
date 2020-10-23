# Permissions
[Back to uhcplus](/wiki/plugins/uhcplus/index.md)

#### The following permissions are automatically granted to operators
- uhcp.\*: Grants access to all UHCPlus commands.
- uhcp.preset.\*: Grants the player access to all /uhcp preset <arguments> commands.
    - uhcp.preset.create: Allows the player to create a new preset.
    - uhcp.preset.delete: Allows the player to delete a preset.
    - uhcp.preset.list: Allows the player to list existing presets.
    - uhcp.preset.load: Allows the player to load a preset.
    - uhcp.preset.options: Allows the player to modify options for the loaded preset.
    - uhcp.preset.seeloaded: Allows the player to see which preset is currently loaded.
    - uhcp.preset.setdefault: Allows the player to set the default preset.
    - uhcp.preset.help: Allows the user to access the preset help page.
- uhcp.teams.\*: Grants the player access to all /uhcp teams <arguments> commands.
    - uhcp.teams.getteams: Allows the user to list all the teams.
    - uhcp.teams.randomfill: Allows the user to force resort the teams randomly.
    - uhcp.teams.help: Allows the user to access the teams help page.
    - uhcp.teams.whichteam: Allows the user to see in which team a player is.
    - uhcp.teams.jointeam: Allows the user to join a team.
    - uhcp.teams.teamcount: Shows the amount of teams configured.
- uhcp.broadcast: Allows the use of /broadcast
- uhcp.gui.\*: Grants the player access to all GUIs.
    - uhcp.gui.modules: Allows the user to see and use the Modules gui.
- uhcp.start: Allows the user to start the UHC.
- uhcp.help: Allows the user to see the UHCPlus help page.

#### The following permissions are automatically granted to all users
- uhcp.chat: Allows the use of /chat.
- uhcp.teaminventory: Allows the use of /ti and /teaminventory
- uhcp.coords: Allows the use of /c and /coords
- uhcp.gui.teams: Allows the user to see and use the Teams gui.
- uhcp.gui.recipes: Allows the user to see and use the Recipes gui.
- uhcp.version: Allows the user to use the /version command
