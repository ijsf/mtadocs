Gets the current traffic light state. This state controls the traffic light colors. For instance, state **1** will cause the north and south traffic lights to be amber, and the ones left and east will turn red.

Syntax
------

``` lua
int getTrafficLightState ( )
```

### Returns

Returns the current [state](/docs/traffic_light_states.md "wikilink") of the traffic lights.

Example
-------

This example causes all traffic lights to be out of order. (flashing amber)

``` lua
function handleTrafficLightsOutOfOrder()
    -- See if the lights are currently off
    local lightsOff = getTrafficLightState() == 9
    
    if lightsOff then
        -- If they're off, turn them on
        setTrafficLightState(6)
    else
        -- If they're on, turn them off
        setTrafficLightState(9)
    end
end
-- Repeat it every half a second
setTimer(handleTrafficLightsOutOfOrder,500,0)
```

See Also
--------
