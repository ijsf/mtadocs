This function returns a float that contains the current gravity for the specified [player](/docs/player.md "wikilink").

Syntax
------

``` lua
float getPlayerGravity ( player thePlayer )
```

### Required Arguments

-   **thePlayer:** The [player](/docs/player.md "wikilink") whose gravity you want to check

### Returns

Returns a [float](/docs/float.md "wikilink") indicating the player's gravity, or *false* if the player is invalid. Default value is 0.008.

Example
-------

This example outputs the gravity of the player who entered the 'showGravity' command.

``` lua
function showGravity ( thePlayer )
    local gravity = getPlayerGravity ( thePlayer )
    outputChatBox ( "Your gravity: " .. tostring(gravity), thePlayer )
end
addCommandHandler ( "showGravity", showGravity )
```

See Also
--------
