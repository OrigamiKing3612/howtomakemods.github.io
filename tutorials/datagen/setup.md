# Setting up Data Generation

1. Open your `datagen.TemplateModDatagen` class.
2. Inside the `onInitializeDataGenerator` method
   1. If this doesn't exist implement the `DataGeneratorEntrypoint` from the `net.fabricmc.fabric.api.datagen.v1` package. And implement methods. 
3. Add this line `FabricDataGenerator.Pack pack = fabricDataGenerator.createPack();` You need the `pack` to add datagen providers.
4. Open your `fabric.mod.json` and make sure you have the `fabric-datagen` entrypoint. Go to the setup page to do this.
5. You have now set up fabric datagen!