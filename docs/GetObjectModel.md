This function retrieves the model ID of a specified object.

Syntax
------

``` lua
int getObjectModel ( object theObject )
```

### Required Arguments

-   **theObject:** The object which you wish to retrieve the model ID of

### Returns

Returns an *int* with the object model id, or *false* if it isn't a valid object.

Example
-------

This example destroys a haystack when a player targets it.

``` lua
function onPlayerTargeted ( targetElem )
    if ( getElementType ( targetElem ) == "object" ) and ( getObjectModel ( targetElem ) == 3374 ) then
        destroyElement ( targetElem )
    end
end
addEventHandler ( "onPlayerTarget", getRootElement(), onPlayerTargeted )
```

This example outputs the model id of objects the player is targeting.

``` lua
function onPlayerTargeted ( targetElem )
    if ( getElementType ( targetElem ) == "object") then
        outputChatBox ( getObjectModel(targetElem) )
    end
end
addEventHandler ( "onPlayerTarget", getRootElement(), onPlayerTargeted )
```

See Also
--------
