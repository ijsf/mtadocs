Object rotation can be retrieved from objects in mapfiles or objects that are created in scripts.

Syntax
------

``` lua
float float float getObjectRotation ( object theObject )       
```

### Required Arguments

-   **theObject:** The object whose rotation will be retrieved

### Returns

Returns three *float*s if object exists, *false* in the first variable and *nil* in the other two if it's invalid.

Example
-------

If a player points at an object with a gun, its rotation will appear in the chat box.

<section name="Server" class="server" show="true">
``` lua
function onPlayerTargeted ( targetElem )
    if ( isElement(targetElem) and getElementType(targetElem) == "object" ) then
        local x,y,z = getObjectRotation ( targetElem )
        outputChatBox ( "Object rotation: " .. x .. " " .. y .. " " .. z, source )
    end
end
addEventHandler ( "onPlayerTarget", getRootElement(), onPlayerTargeted )
```

</section>
<section name="Client" class="client">
``` lua
function onPlayerTargeted ( targetElem )
    if ( isElement(targetElem) and getElementType (targetElem) == "object" ) then
        local x,y,z = getObjectRotation ( targetElem )
        outputChatBox ( "Object rotation: " .. x .. " " .. y .. " " .. z )
    end
end
addEventHandler ( "onClientPlayerTarget", getRootElement(), onPlayerTargeted )
```

</section>
See Also
--------
