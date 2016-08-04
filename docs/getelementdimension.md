This function allows you to retrieve the dimension of any element. The dimension determines what/who the element is visible to.

Syntax
------

``` lua
int getElementDimension ( element theElement )
```

### Required Arguments

-   **theElement:** The element in which you'd like to retrieve the dimension of.

### Returns

Returns an integer for the dimension if **theElement** is valid, *false* otherwise.

Example
-------

This example puts all vehicles with drivers in dimension 1, while all other vehicles are in dimension 0. This would have the effect of making on-foot players invisible to drivers, and vice versa. It'd also make entering a vehicle as passenger after the driver has entered impossible, as the vehicle would appear to vanish to any on foot players.

<section show="true" name="Server" class="server">
``` lua
function onPlayerEnterVehicle ( theVehicle, seat, jacked )
    if ( getElementDimension ( source ) == 0 and seat == 0 ) then -- if the player is in dimension 0 and is entering the driver seat
        setElementDimension ( source, 1 )     -- set his dimension to 1
        setElementDimension ( theVehicle, 1 ) -- set his vehicle's dimension to 1 as well
    end
end
addEventHandler ( "onPlayerVehicleEnter", root, onPlayerEnterVehicle )
 

function onPlayerExitVehicle ( theVehicle, seat, jacker )
    if ( getElementDimension ( source ) == 1 and seat == 0 ) then -- if the player is in dimension 1 and was in the driver's seat
        setElementDimension ( source, 0 )     -- set his dimension back to 0
        setElementDimension ( theVehicle, 0 ) -- set his vehicle's dimension back to 0 as well
    end
end
addEventHandler ( "onPlayerVehicleExit", root, onPlayerExitVehicle )
```

</section>
See Also
--------
