This function checks if the specified [player](/docs/player.md "wikilink") is ducked (crouched) or not.

Syntax
------

``` lua
bool isPlayerDucked ( player thePlayer )
```

### Required Arguments

-   **thePlayer**: A [player](/docs/player.md "wikilink") object referencing the specified player

### Returns

Returns *true* if the player is ducked, *false* otherwise.

Example
-------

This example checks if a random player is ducked or not, and if so displays a message in the chat box.

``` lua
aPlayer = getRandomPlayer ( )
if ( isPlayerDucked ( aPlayer ) ) then
    outputChatBox ( getClientName ( aPlayer ) .. " is currently crouching." )
end
```

See Also
--------
