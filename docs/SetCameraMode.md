This function allows you to set a player's camera to either follow him or be fixed at a certain position.

Syntax
------

``` lua
bool setCameraMode ( player thePlayer, string mode )
```

### Required Arguments

-   **thePlayer:** The player whose camera you wish to modify.
-   **mode:** The mode to be set. It has the following possible values:
    -   **“player”:** Sets the camera to follow a player.
    -   **“fixed”:** Fixes the camera in a set position/rotation.

### Returns

Returns a [bool](/docs/bool.md "wikilink") with a value of *true* if the function was successful, *false* otherwise.

Example
-------

``` lua
function spawnScreen ( source )
        setCameraMode ( source, "fixed" )                                     -- Make the camera fixed (instead of following the player)
        setTimer ( setCameraPosition, 1000, 1, source, 160.15, -1951.68, 50 ) -- Set the coordinates of the camera
        setTimer ( setCameraLookAt, 1000, 1, source, 165, -1951.68, 50 )      -- Make the camera look at specified coordinates
        bindKey ( source, "F1", "down", "Spawn as Vagos", spawnVagos )        -- Bind spawn key (function spawnVagos is not given here)
        bindKey ( source, "F2", "down", "Spawn as Aztecs", spawnAztecs )      -- Bind spawn key (function spawnAztecs is not given here)
end
```

See Also
--------
