# How to add a custom item group
1. Make a new package on `modid` called `group`.
2. Make a new Java Class called `ModGroups`.
3. Now make a public static void `register` method.
4. Go to your mods main file and add the `ModGroups.register()` to the `onInitialize` method.
5. Go back to you `ModGroups` class and add this
```java
public static final RegistryKey<ItemGroup> EXAMPLE_GROUP = RegistryKey.of(RegistryKeys.ITEM_GROUP, new Identifier(TemplateModMain.MOD_ID, "example_group"));
```
6. Now we need to make the group inside the register method.
```java
        Registry.register(Registries.ITEM_GROUP, EXAMPLE_GROUP, FabricItemGroup.builder()
                .displayName(Text.translatable("item_group.modid.example_group")) // translation key
                .icon(() -> new ItemStack(ModItems.TEMPLATE_ITEM)) // Item on the group tab
                .entries((context, entries) -> {
                    entries.add(ModItems.TEMPLATE_ITEM);
                }).build());
```
Here are the imports
```java
import net.fabricmc.fabric.api.itemgroup.v1.FabricItemGroup;
import net.minecraft.item.ItemGroup;
import net.minecraft.item.ItemStack;
import net.minecraft.registry.Registries;
import net.minecraft.registry.Registry;
import net.minecraft.registry.RegistryKey;
import net.minecraft.registry.RegistryKeys;
import net.minecraft.text.Text;
import net.minecraft.util.Identifier;
```
7. Add Items in the group by `entries.add(ITEM_HERE)`
8. Add the `item_group.modid.example_group` to your lang file and that's it!