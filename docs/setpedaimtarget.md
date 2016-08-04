This function allows you to set a ped's aim target to a specific point. If a ped is within a certain range defined by [getPedTargetStart](/docs/getpedtargetstart.md "wikilink") and [getPedTargetEnd](/docs/getpedtargetend.md "wikilink") he will be targeted and shot.

*Note: If you wish to make a ped shoot you must use this in conjunction with an equipped weapon and [setPedControlState](/docs/setpedcontrolstate.md "wikilink").*

Syntax
------

``` lua
bool setPedAimTarget ( ped thePed, float x, float y, float z )
```

### Required Arguments

-   **thePed:** The ped whose target you want to set. Only peds and remote players will work; this function has no effect on the local player.
-   **x:** The x coordinate of the aim target point.
-   **y:** The y coordinate of the aim target point.
-   **z:** The z coordinate of the aim target point.

### Returns

Returns *true* if the function was successful, *false* otherwise.

Example
-------

``` lua
function createPedAndsetHisAimTarget ()
        local ped = createPed (0, 0, 0, 5 ) -- create a ped, who looks like cj, in the middle of the map
        setPedAimTarget ( ped, 10, 10, 5 ) -- set the ped's target to a point in North-East
end
```

See Also
--------
