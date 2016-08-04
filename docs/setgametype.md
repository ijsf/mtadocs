This function sets a string containing a name for the game type. This should be the game-mode that is active, for example “Capture The Flag” or “Deathmatch”. This is then displayed in the server browser and external server browsers.

**It should be noted that [mapmanager](/docs/mapmanager.md "wikilink") handles this automatically for gamemodes that utilise the map/gamemode system.**

Syntax
------

``` lua
bool setGameType ( string gameType )
```

### Required Arguments

-   **gameType:** A string containing a name for the game mode, or *false* to clear it.

### Returns

Returns *true* if the game type was set, *false* if an invalid argument was passed to the function.

Example
-------

This example sets the game type to *Capture The Flag*.

``` lua
setGameType ( "Capture The Flag" )
```

Example 2
---------

This example add command to change Game Type.

``` lua
function setNewGameType( source, commandName, newGameType )
    local oldGameType = getGameType() -- check old Game Type
    setGameType( newGameType ) -- set new Game Type
    outputChatBox( "Game Type " .. oldGameType .. " changed to " .. newGameType .. ".", getRootElement(), 255, 128, 0 )
end
addCommandHandler( "setgametype", setNewGameType )
```

See Also
--------
