Adds a row to a grid list, and optionally add simple text items with your rows. Use [guiGridListSetItemText](/docs/guiGridListSetItemText.md "wikilink") to add row headers.

Syntax
------

``` lua
int guiGridListAddRow ( element gridList )
```

### Required Arguments

-   **gridList:** The grid list you want to add a row to

### Optional Arguments

### Returns

Returns the row id if it has been created, *false* otherwise.

Example
-------

This example creates a player list on the right side of the screen and fills it with the names of the connected players.

``` lua
function clientsideResourceStart ()
        local playerList = guiCreateGridList ( 0.80, 0.10, 0.15, 0.60, true ) -- Create the grid list
        local column = guiGridListAddColumn( playerList, "Player", 0.85 ) -- Create a 'players' column in the list
        if ( column ) then -- If the column was successfully created
                for id, playeritem in ipairs(getElementsByType("player")) do 
                --Loop through all the players, adding them to the table
                        local row = guiGridListAddRow ( playerList )
                        guiGridListSetItemText ( playerList, row, column, getPlayerName ( playeritem ), false, false )
                end
        end
end
addEventHandler ( "onClientResourceStart", getRootElement(), clientsideResourceStart )
```

See Also
--------
