This function allows restoring of world object,which was removed with [RemoveWorldModel](/docs/removeworldmodel.md "wikilink").

Syntax
------

``` lua
bool restoreWorldModel ( int modelID, float radius, float x, float y, float z [, int iInterior = -1 ] )
```

### Required Arguments

-   **modelID:** A whole integer specifying the GTASA object model ID.
-   **radius:** A floating point number representing the radius that will be eliminated.
-   **x:** A floating point number representing the X coordinate on the map.
-   **y:** A floating point number representing the Y coordinate on the map.
-   **z:** A floating point number representing the Z coordinate on the map.

### Returns

Returns *true* if the world object was restored, *false* otherwise.

Requirements
------------

Example
-------

Remove every lamp post (object 1226) besides Grove Street.

``` lua
removeWorldModel(1226, 4000, 0, 0, 0, -1)
restoreWorldModel(1226, 50, 2489, -1665, 13, -1)
```

Changelog
---------

See Also
--------
