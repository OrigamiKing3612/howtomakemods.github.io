## How to add a Block
1. Now open your Main file, for me, it is `TemplateModMain` we will come back to this file soon.
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
public static final Block TEMPLATE_BLOCK = registerBlock("template_block", new Block(FabricBlockSettings.create().strength(0.5f).requiresTool().sounds(BlockSoundGroup.METAL).mapColor(MapColor.WHITE)));
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
16. On the side of the screen where the `gradle` tab is click that. Click `Tasks`/`fabric` then double-click the `runClient`.
17. When the game is loaded open the chat and `/give` your block