# Kits
[Back to uhcplus](/wiki/plugins/uhcplus/index.md)

Kits allows you to give items to players when the UHC starts. Kits are a collection of these items. Metadata (e.g custom names) is supported!

## Creating a kit
1. Put all the items you want the kit to have in your inventory, and nothing more.
2. Use ``/uhcp kits create <kitname>`` to create a kit with the specified name.
3. Your kit is now created! It can be enabled or disabled using the Kits gui, not with commands as of yet.

## Modifying a kit
1. Put all items you want the kit to have in your inventory, and nothing more.
2. Use ``/uhcp kits modify <kitname>`` to modify the kit with the specified name
3. You have now modified the kit!

## Other Kit commands
- ``/uhcp kits list`` This command will list all available kits
- ``/uhcp kits remove <kitname>`` This command will remove the kit with the specified name
- ``/uhcp kits help`` This command will give you the help page for Kits

## Permissions
- ``uhcp.kits.create`` Create a kit [Default: OP]
- ``uhcp.kits.modify`` Modify a kit [Default: OP]
- ``uhcp.kits.list`` List all available kits [Default: OP]
- ``uhcp.kits.help`` View the Kits help page [Default: OP]
- ``uhcp.kits.remove`` Remove a kit [Default: OP]

## Other info
Kits are stored in ``plugins/UHCPlus/kits/<kitname>.kit``. Do not modify these files!