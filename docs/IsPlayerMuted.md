Use this function to check if a player has been muted.

Syntax
------

``` lua
bool isPlayerMuted ( player thePlayer )
```

### Required Arguments

-   **thePlayer:** The [player](/player.md "wikilink") you are checking.

### Returns

Returns *true* if the player is muted and *false* otherwise.

Example
-------

``` lua
someguy = getPlayerFromName ( "someGuy" )
if isPlayerMuted ( someguy ) then
   outputChatBox ( "It seems Someguy can't speak." )
end
```

See Also
--------
