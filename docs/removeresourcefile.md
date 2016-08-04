This function removes a file from the resource.

Syntax
------

``` lua
bool removeResourceFile ( resource theResource, string fileName )
```

### Required Arguments

-   **theResource:** The resource element.
-   **fileName:** The filename what you wan't to delete.

### Returns

Returns *true* if file was deleted, otherwise *false* if the resource is in use or the file doesn't exist.

Example
-------

This example removes a .txt file from the resource sx\_remanager(in-game script editor) when started. (TESTED!)

``` lua
addEventHandler("onResourceStart",resourceRoot,function()
    resource = getResourceFromName("sx_resmanager")
    removeResourceFile(resource,"description.txt")
end)
```

See Also
--------
