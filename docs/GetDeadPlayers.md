This function returns a table of all currently dead players on the server.

Syntax
------

``` lua
table getDeadPlayers()
```

### Returns

Returns a table of all the dead players.

Example
-------

This example prints the list of dead players to the chat box.

``` lua
-- Print a list of all the dead players
  deadPlayers = getDeadPlayers ()
  if ( deadPlayers ) then -- if we got the table
    deadPlayersList = "none"
    -- Loop through the table
    for playerKey, playerValue in deadPlayers do
      -- add their name to the list
      if ( deadPlayersList == "none" ) then
        deadPlayersList = getPlayerName ( playerValue )
      else
        deadPlayersList = deadPlayersList .. ", " .. getPlayerName ( playerValue )
      end
    end
    outputChatBox ( "Dead Players: " .. deadPlayersList )    
  end
```

See Also
--------

[ru:getDeadPlayers](/ru:getDeadPlayers.md "wikilink")
