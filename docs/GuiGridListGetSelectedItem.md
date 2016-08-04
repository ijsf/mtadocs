This function returns the row and colum indexes of the selected item in a grid list.

Syntax
------

``` lua
int, int guiGridListGetSelectedItem ( element gridList )
```

### Required Arguments

-   **gridList:** the grid list you want to know the selected row index of

### Returns

Returns the row and column indexes of the selected item if the specified grid list is valid and has a selected item, (-1, -1) if no item is selected, *false* otherwise.

Example
-------

This code creates a grid list and fills it with the names of the connected players. When the user selects an item, its text (the player name) will be output in the chat box.

``` lua
function createPlayerList ()
        -- Create the grid list
        playerList = guiCreateGridList ( 0.80, 0.10, 0.15, 0.60, true )
        -- Create a players column in the list
        local column = guiGridListAddColumn( playerList, "Player", 0.85 )
        if ( column ) then         -- If the column has been created, fill it with players
                for id, playeritem in ipairs(getElementsByType("player")) do
                        local row = guiGridListAddRow ( playerList )
                        guiGridListSetItemText ( playerList, row, column, getPlayerName ( playeritem ), false, false )
                end
                addEventHandler ( "onClientGUIClick", playerList, click )
        end
end
addEventHandler ( "onClientResourceStart", resourceRoot, createPlayerList )

function click ( button, state, sx, sy, x, y, z, elem, gui )
        -- if state is down ( not to trigger the function twice on mouse button up/down), clicked gui and the element is our player list
        if ( ( state == "down" ) and ( gui == true ) and ( source == playerList ) ) then
                -- get the player name from the selected row, first column 
                local playerName = guiGridListGetItemText ( playerList, guiGridListGetSelectedItem ( playerList ), 1 )
                outputChatBox ( playerName )     -- output it to chat box
        end
end
```

See Also
--------
