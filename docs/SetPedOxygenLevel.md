This function allows you to set the oxygen level of a [ped](/ped.md "wikilink").

Syntax
------

``` lua
bool setPedOxygenLevel ( ped thePed, float oxygen )
```

### Required Arguments

-   **thePed**: the [ped](/ped.md "wikilink") whose oxygen level you want to modify.
-   **oxygen**: the amount of oxygen you want to set on the [ped](/ped.md "wikilink"). Native values are from 0 to 1000. Each of the stamina (22) and underwater stamina (225) [stat](/Template:Stats.md "wikilink") maximum adds a bonus of 1500. So the maximum oxygen level is 4000.

### Returns

Returns *true* if the oxygen level was changed succesfully. Returns *false* if an invalid ped and/or oxygen level was specified.

Example
-------

This example fills the local player's oxygen.

``` lua
function fillOxygen ( command )
    local maxOxygen = math.floor ( 1000 + getPedStat ( localPlayer, 22 ) * 1.5 + getPedStat ( localPlayer, 225 ) * 1.5 )
    setPedOxygenLevel ( localPlayer, maxOxygen )
end
addCommandHandler ( "filloxygen", fillOxygen )
```

See Also
--------
