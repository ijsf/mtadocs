Toggles whether you want the traffic lights to be locked. If the lights are locked, it means they won't change unless you do [setTrafficLightState](/setTrafficLightState.md "wikilink").

Syntax
------

``` lua
bool setTrafficLightsLocked ( bool toggle )
```

### Required Arguments

-   **toggle**: A [bool](/bool.md "wikilink") indicating whether you want the traffic lights to change automatically, or not

### Returns

Returns *true* if the successful, *false* otherwise.

Example
-------

This example toggles traffic lights between 'locked' and 'unlocked'.

``` lua
function toggleTrafficLights()
    if areTrafficLightsLocked() then -- See if traffic lights are currently locked
    setTrafficLightsLocked(false) -- unlock traffic lights if they are currently locked
    else
    setTrafficLightsLocked(true) -- lock traffic lights if they are not locked
    end
end
-- add command handler for command which toggles lights
addCommandHandler("toggletrafficlights",toggleTrafficLights)
```

See Also
--------
