Sets the current traffic light state. This state controls the traffic light colors. For instance, state **1** will cause the north and south traffic lights to be amber, and the ones left and east will turn red.

Syntax
------

``` lua
bool setTrafficLightState ( int state )
```

``` lua
bool setTrafficLightState ( string state )
```

``` lua
bool setTrafficLightState ( string colorNS, string colorEW )
```

### Required Arguments

-   **state**: If an integer is provided, the [state](/docs/Traffic_light_states.md "wikilink") you wish to use (possible values: 0-9). Else, one of the following strings:
    -   **auto**: Sets the traffic lights default behavior (switches the colors automatically).
    -   **disabled**: Turns traffic lights off.

Alternatively, you can provide two string parameters (**colorNS** and **colorEW**) with the colors for north-south and east-west traffic lights respectively. Valid colors are:

-   **green**
-   **yellow**
-   **red**

### Returns

Returns *true* if the state was successfully set, *false* otherwise.

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
