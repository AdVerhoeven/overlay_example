# overlay_example
Example datapack using overlays

## How to use the demo
Steps:
1. Launch your version of minecraft (1.20+) create a new world and add the overlay_example_pack folder (or a .zip of its contents) to the datapacks folder of the new world. (either at creation of the world or after)
2. The datapack only has one mcfunction, which should be added to minecraft:load for whichever overlay is active.
3. Once in the world call /datapack list to see if the datapack loaded correctly, if not, go back to step 1
4. If the datapack shows, you can verify which overlay is active by calling /reload

Remarks:
>Note that in this example formats 45 to 48 will run on the 1_21 overlay and also include a data/minecraft/tags/function/load.json which is indeed a change from the default/old way data/minecraft/tags/function**s**/load.json

>Any function in load.json will trigger when calling /reload (it wont trigger on your initial load into the world, that is inherent to minecraft:load itself)

## helpful links
- https://minecraft.wiki/w/Pack_format#List_of_data_pack_formats (this is the full list, helpful if you want be truly precise with your ranges)
- https://misode.github.io/pack-mcmeta/ (must know for anyone working on datapacks)
- https://minecraft.wiki/w/Data_pack (note that this usually only reflects the *latest* version)


## Useful trick
If you want to update the entire datapack without having to then copy the changes to each different world you can create a Junction or Symbolic Link.

For windows one can use the following powershell command:

`New-Item -ItemType Junction -Path [.minecraft/saves/your_save/datapacks/some_empty_folder] -Target [the_root_folder_of_your_datapack]`

By creating a shortcut or using a different command that results in a symbolic link you will force yourself to also add the **allowed_symlinks.txt** file in the root folder of minecraft, this should be `%AppData%/roaming/.minecraft` if you just use the defaults. On windows I would simply avoid this and use the Junction method above.

Whether you have used a symlink or Junction once it has been setup it will now allow you to reload changes in the folder specified as the -Target just by calling reloading your world with /reload, unless you are using enchantments and other experimental features that require you to close and open your world (you have to restart the local server your world runs on)

