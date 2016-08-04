This function adds a new empty mapfile to an existing resource.

Syntax
------

``` lua
xmlnode addResourceMap ( string filePath, [ int dimension = 0 ] )
```

### Required Arguments

-   **filePath:** The [filepath](/docs/filepath.md "wikilink") of the resource map in the following format: **":resourceName/path"**. 'resourceName' is the name of the resource the map file will be in, and 'path' is the path from the root directory of the resource to the file.

  
For example, if you want to create a map file named 'manycars.map' in the resource 'cdm', it can be created from another resource this way: *addResourceMap(":cdm/manycars.map")*.

If you want to create the map file in the current resource, only the file path is necessary, e.g. *addResourceMap(“manycars.map”)*.

**NOTE:** You can't add a map to a running resource.

### Optional Arguments

-   **dimension:** the [dimension](/docs/dimension.md "wikilink") in which the map's objects will be placed.

### Returns

Returns the new map's root [xmlnode](/docs/xmlnode.md "wikilink") if the map was added successfully, *false* otherwise.

Example
-------

This example just adds a map to a gamemode resource called “cdm”.

``` lua
/New.map",0)
```

See Also
--------
