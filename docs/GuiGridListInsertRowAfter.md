This allows you to insert a new row after a specified row, and simultaneously set text. Good for inserting new rows in the middle of existing rows.

Syntax
------

``` lua
int guiGridListInsertRowAfter ( element gridList, int rowIndex )
```

### Required Arguments

-   **gridList:** The grid list you want to add a row to
-   **rowIndex:** Row ID of the row you want to insert the **new row** after.

### Optional Arguments

### Returns

Returns *true* if the row was successfully added, *false* otherwise.

Example
-------

This example would create a gridlist then add the current players in the server and if anyone joins, it would insert a row at the bottom.

``` lua
gridlist = guiCreateGridList(100,100,200,100,false)
guiGridListAddColumn(gridlist,"Players",0.50)
for i,v in ipairs(getElementsByType("player"))do
    guiGridListSetItemText(gridlist,guiGridListAddRow(gridlist),1,getPlayerName(v),false,false)
end
addEventHandler("onClientPlayerJoin",root,function()
    guiGridListSetItemText(gridlist,guiGridListInsertRowAfter(gridlist,guiGridListGetRowCount(gridlist)),1,getPlayerName(source),false,false)--Add row at the bottom of the gridlist and name it the players name
end)
```

See Also
--------
