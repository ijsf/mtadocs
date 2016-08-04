This function sets the starting Z rotation for the specified spawnpoint.

Syntax
------

``` lua
bool setSpawnpointRotation ( spawnpoint theSpawnpoint, float rotation )
```

### Required Arguments

-   **theSpawnpoint:** The spawnpoint element you want to set rotation to.
-   **rotation:** A [float](/docs/float.md "wikilink") rotation value around the Z axis in degrees.

### Returns

Returns *true* if rotation was successfully set, *false* if invalid arguments were passed.

Example
-------

This example randomizes a spawnpoint's rotation every time a player spawns on it.

``` lua
-- we define our randomizing function
function randomizeSpawnpointRotation()
    -- we obtain a new value between 0 and 360 (math.random() generates numbers between 0 and 1)
    local newRotation = math.random() * 360
    -- we set it as the new rotation for the source spawnpoint
    call(getResourceFromName("spawnmanager"), "setSpawnpointRotation", source, newRotation )
end
-- we attach it as a handler for "onSpawnpointUse"
addEventHandler("onSpawnpointUse", getRootElement(), randomizeSpawnpointRotation)
```
