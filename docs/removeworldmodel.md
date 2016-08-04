This function is used to remove a world object.

Syntax
------

``` lua
 )
```

### Required Arguments

-   **modelID:** A whole integer specifying the GTASA object model ID.
-   **radius:** A floating point number representing the radius that will be eliminated.
-   **x:** A floating point number representing the X coordinate on the map.
-   **y:** A floating point number representing the Y coordinate on the map.
-   **z:** A floating point number representing the Z coordinate on the map.

### Optional Arguments

### Returns

Returns *true* if the [object](/docs/object.md "wikilink") was removed, *false* if invalid arguments were passed.

Requirements
------------

Example
-------

This example will removes buildings on BigEar:

``` lua
removeWorldModel(16617,1000,-300,1556,75) --lod
removeWorldModel(16616,1000,-300,1556,75) --lod
removeWorldModel(16615,1000,-300,1556,75) --lod
removeWorldModel(16138,1000,-300,1556,75) -- model
```

This example removes CJ house:

``` lua
for i=700,20000 do
    removeWorldModel(i,10,2494,-1696,17)
end
```

This server script example removes all models, everywhere:

``` lua
for i=550,20000 do
    removeWorldModel(i,10000,0,0,0)
end
setOcclusionsEnabled(false)  -- Also disable occlusions when removing certain models
setWaterLevel(-5000)         -- Also hide the default water as it will be full of holes
```

Changelog
---------

See Also
--------
