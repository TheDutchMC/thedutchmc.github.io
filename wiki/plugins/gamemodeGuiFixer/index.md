# GamemodeGuiFixer
This plugin tackles a slight issue in Minecraft on Spigot/CraftBukkit/Paper servers

### Download
Downloads can be found [here](https://github.com/TheDutchMC/GamemodeGuiFixer/releases)

### What's the problem
So, on vanilla Minecraft the concept of permissions doesn't really exist. There's OP, and non-OP. Of course, on Spigot servers there is more than that.  
On Spigot, permission nodes exist. E.g ``someCoolPlugin.someCoolCommand`` will give the player access to ``/someCoolCommand`` from the plugin ``someCoolPlugin``.  

Likewhise, for `/gamemode`, there are permission nodes as well. However, the GUI (`F3 + F4`) and `F3 + N` for this doesn't adhere to the Spigot way of doing permissions,
it follows the way vanilla Minecraft way. This means that if you can do `/gamemode`, but aren't OP, you can not use these two super neat features

This plugin solves this, if you've got permission to use `/gamemode`, but are not OP, and this plugin is installed, you can use these two features!

### Supported Minecraft versions
- 1.16.1
- 1.16.2

### Support
Support will be exclusively provided on my Discord [here](https://discord.gg/xE3FcGj)
