# How to make mods
1. To make a mod for Minecraft you need
    1. Typing skills
    2. Java installed on your computer (you probably have java)
    3. IntelliJ IDEA [download](https://www.jetbrains.com/idea/download/)
    4. Some java knowledge (I will teach you as we go)
2. Ok now that you have that go [here](https://fabricmc.net/develop/template/). 
3. Then choose the mod name and package. 
    1. The mod package would be unique to you, so use a domain name(if you own one) or `net.[your Minecraft username].mcmods.(modid)` or `name.modid`.
    2. For example this is mine `net.origamiking.mcmods.(modid)`
    3. Then choose Minecraft Version 1.19.3. Now the checkboxes at the bottom, check the `Data Generation`, and uncheck the `Split client and common sources`. Then download the zip file. 
    4. Unzip the file and put it somewhere you will remember. 
    5. You can also rename the folder what ever you want
    6. Now open the folder in IntelliJ.
7. Now let IntelliJ index everything this shouldn’t take long
8. So now open up the `java` file if it is not already
8. Then on the `ExampleMod.java` file press shift and F6 or right `click-refractor-rename` to rename the file. Rename it to the `[modname]Main` you do not need to write the `.java`.
    1. For example if my mods name is [OrigamiKings Enhancement Mod](https://github.com/OrigamiKing3612/OrigamiKings-Enhancement-Mod) then it would be (if I shorten it)`OemMain`
9. 
