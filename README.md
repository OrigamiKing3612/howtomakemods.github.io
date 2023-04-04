# How to make mods
## How to Setup a mod
1. To make a mod for Minecraft you need
    1. Typing skills
    2. Java installed on your computer (you probably have java)
    3. IntelliJ IDEA ([download](https://www.jetbrains.com/idea/download/))
    4. Some java knowledge
2. Ok now that you have that go [here](https://fabricmc.net/develop/template/). 
3. Then choose the mod name and package. 
    1. The mod package would be unique to you, so use a domain name (if you own one) or `net.[your Minecraft username].mcmods.(modid)` or `name.modid`.
    2. For example this is mine `net.origamiking.mcmods.(modid)`
    3. Then choose Minecraft Version 1.19.4. Now the checkboxes at the bottom, check the `Data Generation`, and uncheck the `Split client and common sources`. Then download the zip file. 
    4. Unzip the file and put it somewhere you will remember. 
    5. You can also rename the folder whatever you want
    6. Now open the folder in IntelliJ.
7. Now let IntelliJ index everything this shouldn’t take long
8. So now open up the `java` file if it is not already
8. Then on the `ExampleMod.java` file press shift and F6 or right `click-refractor-rename` to rename the file. Rename it to the `[modname]Main` you do not need to write the `.java`.
    1. For example if my mods name is [OrigamiKings Enhancement Mod](https://github.com/OrigamiKing3612/OrigamiKings-Enhancement-Mod) then it would be (if I shorten it)`OemMain`
    2. For this it will be the TemplateModMain
9. Now you can delete all the comments (the grayed out lines with `//`)
10. Now go to the `public static final Logger LOGGER = LoggerFactory.getLogger("template-mod");` line and change the `template-mod` to your mod-id
11. Now above the last line we just edited add this `public static final String MOD_ID = "mod-id";` **NOTE: where ever you see mod-id or modid reaplace that with your modid.**
12. Add a new package called `datagen` 
    1. right-click the mod-id folder, now move the `[modname]DataGenerator` to that package.
    2. Also rename the same file to `[modname]Datagen`
13. Now go to your `fabric.mod.json` and change the things to match your mod now
    1. it should look something like this
    ```json
    {
        "schemaVersion": 1,
        "id": "template-mod",
        "version": "${version}",
        "name": "Template Mod",
        "description": "This is an example description! Tell everyone what your mod is about!",
        "authors": [
            "Your name"
        ],
        "contact": {
            "homepage": "put something in here",
            "sources": "or not"
        },
        "license": "MIT ", //(or other)
        "icon": "assets/template-mod/icon.png",
        "environment": "*",
        "entrypoints": {
            "main": [
                "net.origamiking.mcmods.templatemod.TemplateModMain"
            ],
            "fabric-datagen": [
                "net.origamiking.mcmods.templatemod.datagen.TemplateModDatagen"
            ]
        },
        "mixins": [
            "template-mod.mixins.json"
        ],
        "depends": {
            "fabricloader": ">=0.14.17",
            "minecraft": "~1.19.4",
            "java": ">=17",
            "fabric-api": "*"
        },
        "suggests": {
            "another-mod": "*"
        }
    }
    ```
14. Now go to the `gradle.properties` and change the `maven_group` to match your mod if it doesn't
15. Then if you did change something press the refresh gradle button that looks like an elephant.

## How to add an Block
1. Now open your Main file, for me it is `TemplateModMain` we will come back to this file soon.
2. Now on the `modid` package/folder right-click that and add a new package. Type in `blocks`
3. Now on the `blocks` package make a new Java class and name it `ModBlocks`.
4. In that file add this inside the `ModBlocks` class. Replace the `TemplateModMain` with your main file
```java
    public static Item registerBlockItem(String id, Block block) {
        return Registry.register(Registries.ITEM, new Identifier(TemplateModMain.MOD_ID, id), new BlockItem(block, new Item.Settings()));
    }
    public static Block registerBlock(String id, Block block) {
        registerBlockItem(id, block);
        return Registry.register(Registries.BLOCK, new Identifier(TemplateModMain.MOD_ID, id), block);
    }
    public static void register() {
        TemplateModMain.LOGGER.info("Registering Blocks for " + TemplateModMain.MOD_ID);
    }
```
The imports
```java
import net.minecraft.block.Block;
import net.minecraft.item.BlockItem;
import net.minecraft.item.Item;
import net.minecraft.registry.Registries;
import net.minecraft.registry.Registry;
import net.minecraft.util.Identifier;
```
5. Above the `registerBlockItem` method add this to make a block. Replace the `TEMPLATE_BLOCK` and `template_block` with the name of your block.
    _**TIP when you use tab to complete something, it will auto import what it needs.**_
```java
public static final Block TEMPLATE_BLOCK = registerBlock("template_block", new Block(FabricBlockSettings.of(Material.METAL).strength(0.5f).requiresTool()));
```
6. Now go back to your main java class. Inside the `onInitialize` method make it look like this.
```java
    @Override
    public void onInitialize() {
        LOGGER.info("Starting " + MOD_ID);
        ModBlocks.register();
    }
```
7. Now to add the resource files to give it a texture.
8. Your the files we will make will go here. If the folder is not there make it now
```
Blockstate File: src/main/resources/assets/modid/blockstates/template_block.json
Block Model File: src/main/resources/assets/modid/models/block/template_block.json
Item Model File : src/main/resources/assets/modid/models/item/template_block.json
Block Texture: src/main/resources/assets/modid/textures/block/template_block.png
```
9. In the `blockstates/` directory make a new file and name it `your_block_name.json`
10. Inside that add this 
```json
{
  "variants": {
    "": {
      "model": "modid:block/your_block_name"
    }
  }
}
```
11. Inside the `models/block/` directory make a new file again and name it `your_block_name.json`
12. Inside that add this 
```json
{
  "parent": "minecraft:block/cube_all",
  "textures": {
    "all": "modid:block/your_block_name"
  }
}
```
13. Inside the `models/item/` directory make a new file again and name it `your_block_name.json`
14. Inside that add this 
```json
{
  "parent": "modid:block/your_block_name"
}
```
15. Last but not least inside the `textures/block/` directory add the `.png` of the block.
_**NOTE: the `your_block_name.png` needs to be 16x16 or 32x32 pixels**_
16. On the side of the screen where the `gradle` tab is click that. Click `Tasks`-`fabric` then double click the `runClient`.
17. When the game is loaded open the chat and `/give` your block
## How to add an Item
1. Make a new package inside the modid package name it `items`
2. Inside that make a new java class named `ModItems`
3. Now add this to inside the `ModItems` class
```java
    public static Item registerItem(String name, Item item) {
        return Registry.register(Registries.ITEM, new Identifier(TemplateModMain.MOD_ID, name), item);
        }
    public static void register() {
        TemplateModMain.LOGGER.info("Registering Items for " + TemplateModMain.MOD_ID);
    }
```
Heres the imports
```java
import net.minecraft.item.Item;
import net.minecraft.registry.Registries;
import net.minecraft.registry.Registry;
import net.minecraft.util.Identifier;
```
4. To add an item add this above the `registerItem` method 
```java
    public static final Item TEMPLATE_ITEM = registerItem("template_item", new Item(new FabricItemSettings()));
```
5. Now open your mod's main file and call the `register` method from the `ModItems` inside of the `onInitialize` method in the Main file.
6. To add the texture go to the `assets/modid/textures/items` and add the texture
7. Now go to `assets/modid/models/item` and make a new json file with the same id that your item has for example `template_item.json`.
8. inside that put this
```json
{
  "parent": "minecraft:item/generated",
  "textures": {
    "layer0": "modid:item/template_item"
  }
}
```
9. Now run client and `/give` the item

