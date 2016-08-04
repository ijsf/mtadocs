<lowercasetitle></lowercasetitle>

This function get text selected on gridlist

Syntax
------

``` lua
element guiGridListGetSelectedText( element gridList, int columnIndex )
```

### Required Arguments

-   **gridList**: The grid list element
-   **columnIndex**: column id of the item

### Returns

Returns *string* text of the selected item if the specified grid list is valid and has a selected item, false otherwise.

Code
----

<section name="Client" class="client" show="true">
``` lua

function guiGridListGetSelectedText(gridList, columnIndex)
    local selectedItem = guiGridListGetSelectedItem(gridList)
    if (selectedItem) then
        local text = guiGridListGetItemText(gridList, selectedItem, columnIndex or 1)
        if (text) and not (text == "") then
            return text
        end
    end
    return false
end
```

</section>
Example
-------

This example get player name from gridlist

<section name="Client" class="client" show="true">
``` lua

addEventHandler("onClientResourceStart", resourceRoot,
function ()
    playerList = guiCreateGridList(0.80, 0.10, 0.15, 0.60, true)
    local column = guiGridListAddColumn(playerList, "Player", 0.85)
    if (column) then
        for id, playeritem in ipairs(getElementsByType("player")) do
            local row = guiGridListAddRow(playerList)
            guiGridListSetItemText(playerList, row, column, getPlayerName(playeritem), false, false)
        end
    end
end)
 
addEventHandler("onClientGUIClick", playerList,
function ( )
    local playerName = guiGridListGetSelectedText(playerList)
    outputChatBox("You'r selected player: "..playerName)
end)
```

</section>
Credits
-------

-   **Author:**: WASSIm.

See Also
--------
