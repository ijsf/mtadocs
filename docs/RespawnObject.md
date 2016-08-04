This function respawns a specific object.

Syntax
------

``` lua
bool respawnObject ( object theObject )
```

### Required Arguments

-   **theObject:** an [object](/object.md "wikilink") element

### Returns

-   *true* if the object was sucessfully respawned.
-   *false* if the object is not breakable, or a wrong object was given.

Example
-------

This example prevents objects from despawning. When an object breaks, it gets respawned right away.

``` lua
addEventHandler ( "onClientObjectBreak", getRootElement(),
    function ()
        respawnObject ( source )
    end
)
```

See Also
--------
