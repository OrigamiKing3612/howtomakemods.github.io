# How to make mods
1. To make a mod for Minecraft you need
    1. Typing skills
    2. Java installed on your computer (you probably have java)
    3. IntelliJ IDEA ([download](https://www.jetbrains.com/idea/download/))
    4. Some java knowledge (I will teach you as we go)
2. Ok now that you have that go [here](https://fabricmc.net/develop/template/). 
3. Then choose the mod name and package. 
    1. The mod package would be unique to you, so use a domain name(if you own one) or `net.[your Minecraft username].mcmods.(modid)` or `name.modid`.
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
16. Now that your mod is set up contact OrigamiKing3612 to make a mod.
