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

