This function returns an element of the specified type with the specified index.

Syntax
------

``` lua
element getElementByIndex ( string theType, int index )  
```

### Required Arguments

-   **theType:** the type of the element to be returned. Examples include “player”, “vehicle”, or a custom type.
-   **index:** the element's index (0 for the first element, 1 for the second, etc).

### Returns

Returns the requested [element](/docs/element.md "wikilink"), or *false* if it doesn't exist.

Example
-------

This example outputs the name of the specified vehicle currently existent in the XML tree. For example: 'vehicle 0' would return the first vehicle.

``` lua
function showVehicle(thePlayer, command, index)
    local theVehicle = getElementByIndex("vehicle", tonumber(index))
    if theVehicle then
        outputChatBox("Vehicle " .. index .. " is a: " .. getVehicleName(theVehicle), thePlayer)
    else
        outputChatBox("Vehicle not found.", thePlayer)
    end
end
addCommandHandler("vehicle", showVehicle)
```

See Also
--------
