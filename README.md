# overlay_example
Example datapack using overlays

## Use the demo
Launch your version of minecraft (1.20+) create a new world and add the overlay_example_pack folder (or a .zip of its contents)
The datapack only has one mcfunction, which should be added to minecraft:load for whichever overlay is active Note that in this example formats 45 to 48 will run on the 1_21 overlay and also include a data/minecraft/tags/function/load.json which is indeed a change from the default/old way data/minecraft/tags/function**s**/load.json
Any function in load.json will trigger when calling /reload (it wont trigger on your initial load into the world, that is inherent to minecraft:load itself)

## helpful links
- https://minecraft.wiki/w/Pack_format#List_of_data_pack_formats (this is the full list, helpful if you want be truly precise with your ranges)
- https://misode.github.io/pack-mcmeta/ (must know for anyone working on datapacks)
- https://minecraft.wiki/w/Data_pack (note that this usually only reflects the *latest* version)
