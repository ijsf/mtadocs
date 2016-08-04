With this function you can retrieve the [string](/string.md "wikilink") data associated with an item in a [grid list](/Element/GUI/Gridlist.md "wikilink"). This is not the text that is displayed on the item, but an internal string that you can use to hold extra information about the item.
**Note:** This function will only work **after** you set the item's text using [guiGridListSetItemText](/guiGridListSetItemText.md "wikilink")!

Syntax
------

``` lua
var guiGridListGetItemData ( element gridList, int rowIndex, int columnIndex )
```

### Required Arguments

-   **gridList:** the grid list containing the item you're interested in
-   **rowIndex:** the row index of the item
-   **columnIndex:** the column index of the item

### Returns

Returns the item data of the specified item if succesful, *false* if one of the arguments was invalid.

Example
-------

This example displays a random item data from the gridlist.

``` lua
function clientsideResourceStart ()
    local numberList = guiCreateGridList ( 0.80, 0.10, 0.15, 0.60, true )
    local column = guiGridListAddColumn ( numberList, "Column Title", 0.85 )
    if ( column ) then
        local row = guiGridListAddRow ( numberList )
        local myItem = guiGridListSetItemText ( numberList, row, column, tostring( math.random(0, 10) ^ 100 ), false, false )
        local myItemData = guiGridListGetItemData ( numberList, row, column )
        outputChatBox ( "My gridlist item data: " .. myItemData )
    end
end
addEventHandler ( "onClientResourceStart", resourceRoot, clientsideResourceStart )
```

See Also
--------
