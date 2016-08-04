This function retrieves the current gametype as set by [setGameType](/setGameType.md "wikilink"). The game type is displayed in the server browser next to the server's name.

Syntax
------

``` lua
string getGameType ()
```

### Returns

Returns the gametype as a string. If no gametype is set it returns *nil*.

Example
-------

This example sends a message to player when he joins, if the current game type is Race.

``` lua
function playerJoinHandler( )
   if getGameType() == "Race" then
      outputChatBox( "Ready... Get set... GO!!", source )
   end
end
addEventHandler( "onPlayerJoin", getRootElement(), playerJoinHandler )
```

See Also
--------
