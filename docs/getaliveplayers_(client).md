<lowercasetitle></lowercasetitle>

This function returns all the alive players by a client side, so you can store them into a Gridlist or something like that, faster.

Syntax
------

``` lua
table getAlivePlayers()
```

Code
----

<section name="Function source" class="client" show="true">
``` lua
function getAlivePlayers()
  local alivePlayers = { }
  for i,p in ipairs (getElementsByType("player")) do
    if getElementHealth(p) > 0 then
      table.insert(alivePlayers,p)
    end 
  end
  return alivePlayers
end
```

</section>
Example
-------

<section name="Example" class="client" show="true">
We want to get the alive players and place them into a gridlist.

``` lua
local playerGrid = guiCreateGridList ( 0.80, 0.10, 0.15, 0.60, true ) --Creates the gridlist.
local column = guiGridListAddColumn( playerGrid, "Player", 0.85 ) --Creates a player column in the list.
if column then --If the column suscessfully set...
       local players = getAlivePlayers()
       for id, player in ipairs(players) do
             local row = guiGridListAddRow ( playerGrid ) --Creates a row for each player.
             guiGridListSetItemText ( playerGrid, row, column, getPlayerName ( player ), false, false ) --Fills the row with the name of the player.
       end
end
```

</section>
Original function by **The Kid**.

See Also
--------
