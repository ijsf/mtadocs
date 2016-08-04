This function checks if the specified [ped](/docs/ped.md "wikilink") is choking (coughing) or not. This happens as a result of weapons that produce smoke - smoke grenades, fire extinguisher and the spray can.

Syntax
------

``` lua
bool isPedChoking ( ped thePed )
```

### Required Arguments

-   **thePed**: The [ped](/docs/ped.md "wikilink") you wish to check

### Returns

Returns *true* if the ped is choking, *false* otherwise.

Example
-------

<section class="both" name="Server&Client" show="true">
This example checks if a random player is choking or not, and if so displays a message in the chat box.

``` lua
local players = getElementsByType ( "player" )
local randomPlayer = players[math.random(#players)]
if isPedChoking ( randomPlayer ) then
    outputChatBox ( getPlayerName ( randomPlayer ) .. " is choking.  Keep away from those cigarettes!" )
end
```

</section>
See Also
--------
