Syntax
------

``` lua
bool setVehiclePlateText( element theVehicle, string numberplate )
```

### Required Arguments

-   **theVehicle:** the [vehicle](/docs/vehicle.md "wikilink") whose numberplate you want to change.
-   **numberplate:** a string that will go on the number plate of the car (max 8 characters).

### Returns

Returns *true* if the numberplate was changed successfully, or *false* if invalid arguments were passed

Requirements
------------

Example
-------

``` lua
function PlateText(thePlayer,commandName,text)
    local Vehicle = getPedOccupiedVehicle(thePlayer)
    if Vehicle then
        if text then
            setVehiclePlateText( Vehicle, text )
        else
            outputChatBox("You must enter a message.",thePlayer)
        end
    else
        outputChatBox("You must be in a Vehicle.",thePlayer)
    end
end
addCommandHandler("setplate",PlateText)
```

See Also
--------
