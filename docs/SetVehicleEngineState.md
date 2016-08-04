This function turns a vehicle's engine on or off. Note that the engine will always be turned on when someone enters the driver seat, unless you override that behaviour with scripts.

Syntax
------

``` lua
bool setVehicleEngineState ( vehicle theVehicle, bool engineState )
```

### Required Arguments

-   **theVehicle**: The [vehicle](/vehicle.md "wikilink") you wish to change the engine state of.
-   **engineState**: A boolean value representing whether the engine will be turned on (*true*) or off (*false*).

### Returns

Returns *true* if the vehicle's engine state was successfully changed, *false* otherwise.

Example
-------

<section name="Serverside example" class="server" show="true">
This example will turn off a vehicle's engine when the driver gets out of the car.

``` lua
function turnEngineOff ( theVehicle, leftSeat, jackerPlayer )
    -- if it's the driver who got out, and he was not jacked,
    if leftSeat == 0 and not jackerPlayer then
        -- turn off the engine
        setVehicleEngineState ( theVehicle, false )
    end
end
-- add 'turnEngineOff' as a handler for "onPlayerExitVehicle"
addEventHandler ( "onPlayerVehicleExit", getRootElement ( ), turnEngineOff )
```

</section>
See Also
--------
