This function checks if the specified [player](/docs/player.md "wikilink") is choking (coughing) or not. This happens as a result of weapons that produce smoke - smoke grenades, fire extinguisher and the spray can.

Syntax
------

``` lua
bool isPlayerChoking ( player thePlayer )
```

### Required Arguments

-   **thePlayer**: The [player](/docs/player.md "wikilink") you wish to check

### Returns

Returns *true* if the player is choking, *false* otherwise.

Example
-------

This example checks if a random player is choking or not, and if so displays a message in the chat box.

``` lua
aPlayer = getRandomPlayer ( )
if ( isPlayerChoking ( aPlayer ) ) then
    outputChatBox ( getClientName ( aPlayer ) .. " is choking.  Keep away from those cigarettes!" )
end
```

See Also
--------
