# Data Generate Loot Tables

1. Inside the `datagen` package create a `ModBlockLootTableGenerator` class and extend `FabricBlockLootTableProvider` from `net.fabricmc.fabric.api.datagen.v1.provider;`and implement the methods
2. Now inside the `generate` method type `addDrop(ModBlocks.TEMPLATE_BLOCK)`
   1. If you middle-mouse-click of `addDrop` you can see all the different methods.
   2. For example if you want to make a `slabDrop` you would do this `addDrop(ModBlocks.EXAMPLE_SLAB, slabDrops(ModBlocks.EXAMPLE_SLAB));`3.
3. That's Loot Table Generation!