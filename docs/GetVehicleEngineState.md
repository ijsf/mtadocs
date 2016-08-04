This function returns a vehicle's engine state (on or off).

Syntax
------

``` lua
bool getVehicleEngineState ( vehicle theVehicle )
```

### Required Arguments

-   **theVehicle**: the [vehicle](/vehicle.md "wikilink") you wish to get the engine state of.

### Returns

Returns **true** if the vehicle's engine is started, **false** otherwise.

Example
-------

<section name="Serverside example" class="server" show="true">
This example will switch the vehicle engine state with the command "/switchengine".

``` lua
function switchEngine ( playerSource )
    local theVehicle = getPedOccupiedVehicle ( playerSource )

    -- Check if the player is in any vehicle and if he is the driver
    if theVehicle and getVehicleController ( theVehicle ) == playerSource then
        local state = getVehicleEngineState ( theVehicle )
        setVehicleEngineState ( theVehicle, not state )
    end
end
addCommandHandler ( "switchengine", switchEngine )
```

</section>
See Also
--------
