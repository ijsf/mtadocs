This function retrieves the text from a specific grid list item.

Syntax
------

``` lua
string guiGridListGetItemText ( element gridList, int rowIndex, int columnIndex )
```

### Required Arguments

-   **gridList:** the gridlist containing the item you're interested in
-   **rowIndex:** row id of the item
-   **columnIndex:** column id of the item

### Returns

Returns the text of the item if the arguments are right, *false* otherwise.

Example
-------

**Example 1**: This example creates a gridlist with entries “Hello” and “World!” and chooses randomly which of these two grid list items it will retrieve.

``` lua
function clientsideResourceStart ()
        --Create a gridlist
        local myGridList = guiCreateGridList ( 0.80, 0.10, 0.15, 0.60, true ) 
        --Create columnA on the gridlist
        local columnA = guiGridListAddColumn ( myGridList, "columnA Title", 0.85 ) 
        --Add 2 rows to the grid list
        rowA = guiGridListAddRow ( myGridList )
        rowB = guiGridListAddRow ( myGridList )
        --Create the text "Hello" for rowA, columnA
        guiGridListSetItemText ( myGridList, rowA, columnA, "Hello", false, false )     
        --Create the text "World!" for rowB, columnA
        guiGridListSetItemText ( myGridList, rowB, columnA, "World!", false, false )
        --Choose randomly which grid list item text to retrieve
        getRandomItem = math.random ( 1, 2 )       
        if getRandomItem == 1 then 
                randomItemData = guiGridListGetItemText ( myGridList, rowA, columnA )
        elseif getRandomItem == 2 then
                randomItemData = guiGridListGetItemText ( myGridList, rowB, columnA )
        end
        --Output the randomly retrieved item text
        outputChatBox ( "My gridlist item text: "..randomItemData ) 
end
addEventHandler ( "onClientResourceStart", resourceRoot, clientsideResourceStart )
```

**Example 2**: This example creates a player list on resource start, clicking on it will output the selected player name to the chatbox.

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
addEventHandler ( "onClientResourceStart", getRootElement(), createPlayerList )

function click () 
       local playerName = guiGridListGetItemText ( playerList, guiGridListGetSelectedItem ( playerList ), 1 )
       outputChatBox(playerName)
end
```

See Also
--------
