This class can be found at **“mtasa-blue\\MTA10\_Server\\mods\\deathmatch\\logic\\lua\\CLuaManager.cpp”** and **“mtasa-blue\\MTA10\\mods\\shared\_logic\\lua\\CLuaManager.cpp”**.

Lua definition refactor
-----------------------

Originally, all the Lua definitions were stored in a huge *CLuaFunctionDefs.cpp/h* file, the Lua function names were stored in a huge *CLuaManager.cpp*, and the classes were stored in a huge *CLuaMain.cpp/h*. This refactor moves all the definitions to their own classes (e.g, *CLuaElementDefs.cpp/h*) that also contain methods to add classes (e.g, *CLuaElementDefs::AddClass*), Lua definitions (e.g, *CLuaElementDefs::GetRootElement*), and Lua function names (e.g, *CLuaElementDefs::LoadFunctions*).

This information is to show where certain things are placed for function definitions. As a rule of thumb, if a function takes a player for its first argument you'll find it in the player definitions file (adapt this for whatever class you want).

Backwards compatibility functions remain in **“CLuaFunctionDefs.h”**.

Things with “todo” at the beginning aren't currently done, but are expected to be completed.

<section name="Server" class="server" show="true">
-   (todo) ASE Functions file are \*all\* inside the Server definitions file (including player defs) (currently: ase in CLuaManager, aseplayer in playerdefs)
-   (todo) Admin functions are all inside the server defs file (including kick/banplayer) (currently: kickbanplayer in playerdefs)
-   Inside player definitions (because they only work on players, unless otherwise reasoned)
    -   Sound functions
    -   Cursor functions
    -   Input functions
    -   [showChat](/docs/showChat.md "wikilink")
    -   [outputChatBox](/docs/outputChatBox.md "wikilink")
    -   Console functions (command functions)
-   [getWeaponAmmo](/docs/getWeaponAmmo.md "wikilink") is a player function, but stored in the wepdefs (todo: wepdefs not done yet)

</section>
<section name="Client" class="client" show="true">
The refactor hasn't been started yet.

</section>
### TODO

- Search for oop definition files that shouldn't be in the repo, and delete them.

### Tools

- Convert CLuaOOPDefs to \_OOP.

    CLuaOOPDefs::(.*?)( |,)   to   OOP_$1$2
