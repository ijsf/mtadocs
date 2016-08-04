This function sets the skin that players will spawn with when they spawn at the specified spawnpoint.

Syntax
------

``` lua
bool setSpawnpointSkin ( spawnpoint theSpawnpoint, int skin )
```

### Required Arguments

-   **theSpawnpoint:** The spawnpoint you want to change skin of.
-   **skin:** An [int](/int.md "wikilink") corresponding to the ID of the desired skin. See [Character Skins](/Character_Skins.md "wikilink").

### Returns

Returns *true* if the skin was successfully set, *false* if invalid arguments were passed.

Example
-------

This code alters all existing spawnpoints so everyone spawns as construction workers.

``` lua
-- get a table of all spawnpoints
local allSpawnpoints = getElementsByType("spawnpoint")
-- for each spawnpoint,
for index, spawn in ipairs (allSpawnpoints) do
    -- change the spawn skin to 27
    call(getResourceFromName("spawnmanager"), "setSpawnpointSkin", spawn, 27 )
end
```
