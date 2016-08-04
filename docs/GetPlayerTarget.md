This function is used to get the element a [player](/player.md "wikilink") is currently targeting.

Syntax
------

``` lua
element getPlayerTarget ( player thePlayer )
```

### Required Arguments

-   **thePlayer:** The [player](/player.md "wikilink") whose target you want to retrieve.

### Returns

Returns the [element](/element.md "wikilink") that's being targeted, or *false* if there isn't one.

This is only effective on physical GTA elements, namely:

-   Players
-   Vehicles
-   Objects

Example
-------

This example blows up any vehicle a player targets (aims at).

``` lua
function playerTargetCheck ( )
    local target
    for i, thePlayer in ipairs ( getElementsByType("player") ) do  -- iterate over all players
        target = getPlayerTarget ( thePlayer )                     -- get the target of the current player
        if ( target ) then                                         -- if there was a target
            if ( getElementType ( target ) == "vehicle" ) then     -- and the target is a vehicle
                blowVehicle ( target )                             -- blow it up
            end
        end
    end
end
setTimer ( playerTargetCheck, 1000, 0 )                            -- call the check function every second
```

*Note: A more efficient way to do this would be to use the [onPlayerTarget](/onPlayerTarget.md "wikilink") event.*

See Also
--------
