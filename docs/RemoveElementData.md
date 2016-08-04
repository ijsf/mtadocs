This function removes the [element data](/element_data.md "wikilink") with the given key for that element. The element data removal is synced with all the clients.

Syntax
------

``` lua
bool removeElementData ( element theElement, string key ) 
```

### Required Arguments

-   **theElement:** The [element](/element.md "wikilink") you wish to remove the data from.
-   **key:** The key string you wish to remove.

### Returns

Returns *true* if the data was removed succesfully, *false* if the given key does not exist in the element or the element is invalid.

Example
-------

This will create an element data for know if a player has spawned.

``` lua
function spawn()
    setElementData(source,"spawned",true)
end
addEventHandler ( "onPlayerSpawn", getRootElement(), spawn )
function wasted()
    removeElementData(source,"spawned")
end
addEventHandler ( "onPlayerWasted", getRootElement(), wasted )
```

See Also
--------
