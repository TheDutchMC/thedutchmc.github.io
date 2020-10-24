# HaroTorch
Modded Minecraft's MegaTorch, on Spigot

HaroTorch is a plugin which blocks mob spawns in a 64 block radius (configurable) from a torch (configurable) called the "HaroTorch". Bringing MegaTorch to Spigot!

### Commands
- `/torch give`: [OP] Give yourself a HaroTorch
- `/torch highlight`: [ALL] Highlight all HaroTorches in a 64 block radius (configurable)
- `/torch help`: [ALL] See HaroTorch's help pages. WIP
- `/torch convert`: [OP] Convert from v1 to v2
- `/torch version`: [ALL] Shows you what HaroTorch and NMS version you are running
- `/torch aoe:` [ALL] Spawns a circle of particles on the border of your torch's Area of Effect

### Permissions
- `harotorch.*`: [OP] Grants access to all /torch commands
- `harotorch.give`: [OP] Grants access to /torch give
- `harotorch.convert`: [OP] Grants access to /torch convert
- `harotorch.highlight`: [ALL] Grants access to /torch highlight
- `harotorch.help`: [ALL] Grants access to /torch help
- `harotorch.version`: [ALL] Grants access to /torch version
- `harotorch.aoe`: [ALL] Grants access to /torch aoe

### Recipe
The default recipe is 4 Golden ingots and 1 torch in a plus shaped recipe. However this is configurable.

### Migrating from v1 to v2
It's easy!
1. Make sure you have a backup of your torches.yml file from v1
2. Start your server with both v1 and v2 installed
3. Run /torch convert
4. Shut down your server and remove v1
5. All done :)

### Supported Minecraft versions
All versions above 1.16.2 are supported. However the highlight feature is not supported on all versions.
- 1.16.2
- 1.16.3

### Using your own language
To use your own language, check out this page: [HaroTorch on GitHub](https://github.com/TheDutchMC/HaroTorch/blob/v2/languages/README.md)

### Issues and version requests
If you have found an issue in HaroTorch, have a feature you want implemented, or a version you would like supported, you can ask so here: [HaroTorch GitHub](https://github.com/TheDutchMC/HaroTorch/issues)

### Support
Support will be exclusively provided on my Discord [here](https://discord.gg/xE3FcGj)
