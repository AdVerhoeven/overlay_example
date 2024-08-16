# overlay_example
Example datapack using overlays

## How to use the demo
Steps:
1. Launch your version of minecraft (1.20+) create a new world and add the overlay_example_pack folder (or a .zip of its contents) to the datapacks folder of the new world. (either at creation of the world or after)
2. The datapack only has one mcfunction, which should be added to minecraft:load for whichever overlay is active.
3. Once in the world call /datapack list to see if the datapack loaded correctly, if not, go back to step 1
4. If the datapack shows, you can verify which overlay is active by calling /reload
5. You can verify how the ordering works by changing pack.mcmeta, the format16and_above overlays are nearly identical, but the order inside pack.mcmeta means the bad_practice will actually result in overruling all overlays that came before it except those that support a format above 41 and only if the game is loaded with a version that uses format 42 or higher.
6. This behaviour can be verified as the no_overrule SHOULD NOT apply when your pack_format is 26 exactly, but it SHOULD apply if your pack_format is between 27 and 40. (not 41, as that is in the other overlay)

Remarks:
>Note that in this example formats 45 to 48 will run on the 1_21 overlay and also include a data/minecraft/tags/function/load.json which is indeed a change from the default/old way data/minecraft/tags/function`s`/load.json

>Any function in load.json will trigger when calling /reload (it wont trigger on your initial load into the world, that is inherent to minecraft:load itself)

>The order of overlays matters! Removing the last overlay entry makes a lot of changes for all versions of minecraft prior to those using pack_format 41.

## helpful links
- https://minecraft.wiki/w/Pack_format#List_of_data_pack_formats (this is the full list, helpful if you want be truly precise with your ranges)
- https://misode.github.io/pack-mcmeta/ (must know for anyone working on datapacks)
- https://minecraft.wiki/w/Data_pack (note that this usually only reflects the *latest* version)


## Useful trick
If you want to update the entire datapack without having to then copy the changes to each different world you can create a Junction or Symbolic Link.

For windows one can use the following powershell command:

`New-Item -ItemType Junction -Path [.minecraft/saves/your_save/datapacks/some_empty_folder] -Target [the_root_folder_of_your_datapack]`

By creating a shortcut or using a different command that results in a symbolic link you will force yourself to also add the **allowed_symlinks.txt** file in the root folder of minecraft, this should be `%AppData%/roaming/.minecraft` if you just use the defaults. On windows I would simply avoid this and use the Junction method above.

Whether you have used a symlink or Junction once it has been setup it will now allow you to reload changes in the folder specified as the -Target just by reloading your world with /reload, unless you are using enchantments and other experimental features that require you to close and open your world (you have to restart the local server your world runs on)

