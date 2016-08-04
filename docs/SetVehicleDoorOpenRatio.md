This function sets how much a vehicle's door is open. Doors include the boot/trunk and the bonnet of the vehicle.

Syntax
------

``` lua
bool setVehicleDoorOpenRatio ( vehicle theVehicle, int door, float ratio [, int time = 0] )
```

Required Arguments
------------------

-   **theVehicle:** The [vehicle](/docs/vehicle.md "wikilink") that you wish to change the door open ratio of.
-   **door:** A whole number, 0 (hood), 1 (trunk), 2 (front left), 3 (front right), 4 (rear left), 5 (rear right)
-   **ratio:** The ratio value, ranging from 0 (fully closed) to 1 (fully open).

Optional Arguments
------------------

-   **time:** The number of milliseconds the door should take to reach the value you have specified. A value of 0 will change the door open ratio instantly.

Returns
-------

Returns *true* if the door open ratio was successfully set, *false* if invalid arguments are passed.

Example
-------

This example opens all the doors of the vehicle gradually over 2.5 seconds.

``` lua
addCommandHandler ( "carshowoff", function ( playerSource )
    local vehicle = getPedOccupiedVehicle ( playerSource )
    if vehicle then
        for i=0,5 do
            setVehicleDoorOpenRatio ( vehicle, i, 1 - getVehicleDoorOpenRatio ( vehicle, i ), 2500 )
        end
    end
end )
```

See Also
--------
