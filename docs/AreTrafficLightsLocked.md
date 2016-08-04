Gets whether the traffic lights are currently locked or not. If the lights are locked, it means they won't change unless you do [setTrafficLightState](/setTrafficLightState.md "wikilink").

Syntax
------

``` lua
bool areTrafficLightsLocked ( )
```

### Returns

Returns *true* the traffic lights are currently locked, *false* otherwise.

Example
-------

This example toggles traffic lights between 'locked' and 'unlocked'.

``` lua
function toggleTrafficLights()
    if areTrafficLightsLocked() then -- See if traffic lights are currently locked
    setTrafficLightsLocked(false) -- unlock traffic lights if they are currently locked
    else
    setTrafficLightsLocked(true) -- lock traffic lights if they are not
    end
end
-- add command for toggling traffic lights
addCommandHandler("toggletrafficlights",toggleTrafficLights)
```

See Also
--------

[ru:areTrafficLightsLocked](/ru:areTrafficLightsLocked.md "wikilink")
