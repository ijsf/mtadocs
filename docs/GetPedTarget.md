This function is used to get the element a [ped](/docs/ped.md "wikilink") is currently targeting.

Syntax
------

``` lua
element getPedTarget ( ped thePed )
```

### Required Arguments

-   **thePed:** The [ped](/docs/ped.md "wikilink") whose target you want to retrieve.

### Returns

Returns the [element](/docs/element.md "wikilink") that's being targeted, or *false* if there isn't one.

This is only effective on physical GTA elements, namely:

-   Players
-   Vehicles
-   Objects

Example
-------

<section name="Server" class="server" show="true">
This example blows up any vehicle a player targets (aims at).

``` lua
function playerTargetCheck ( )
    local target
    for i, thePlayer in ipairs ( getElementsByType("player") ) do  -- iterate over all players
        target = getPedTarget ( thePlayer )                        -- get the target of the current player
        if ( target ) then                                         -- if there was a target
            if ( getElementType ( target ) == "vehicle" ) then     -- and the target is a vehicle
                blowVehicle ( target )                             -- blow it up
            end
        end
    end
end
setTimer ( playerTargetCheck, 1000, 0 )                            -- call the check function every second
```

*Note: A more efficient way to do this would be to use the [onPlayerTarget](/docs/onPlayerTarget.md "wikilink") event.*

</section>
See Also
--------
