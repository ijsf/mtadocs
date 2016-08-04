This function allows you to move a player's camera to a specific location if it is fixed (see [setCameraMode](/setCameraMode.md "wikilink")).

Syntax
------

``` lua
bool setCameraPosition ( player thePlayer, float x, float y, float z )
```

### Required Arguments

-   **thePlayer:** The player whose camera you wish to modify. (not needed for clientside scripting)
-   **x:** The x coordinate of the new position.
-   **y:** The x coordinate of the new position.
-   **z:** The x coordinate of the new position.

### Returns

Returns *true* if the function was successful, *false* otherwise.

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
