This function is intended to load data from a loaded XML file into the element tree. This could be used for loading an external map, or part of another map.

Syntax
------

``` lua
element loadMapData ( xmlnode node, element parent )  
```

### Required Arguments

-   **node:** The node that you wish to load into the [element tree](/docs/element_tree.md "wikilink").
-   **parent:** The node you wish to be the parent of the new map data.

### Returns

Returns an [element](/docs/element.md "wikilink") object that corresponds to the root of the new data added, i.e. an element that represents the *node* xmlnode passed to the function. Returns *false* if the arguments are invalid.

Example
-------

This example is a function that you could use to load an arbitary [map file](/docs/map_files.md "wikilink") into the [element tree](/docs/element_tree.md "wikilink").

``` lua
function loadMapFile ( filename )
    node = getResourceConfig ( filename )
    -- Check if the file was loaded ok
    if ( node ) then
        -- Load the loaded xml file into the element tree
        loadMapData ( node, getRootElement() )
        -- Unload the xml file again
        xmlUnloadFile ( node )
    end
end
```

See Also
--------
