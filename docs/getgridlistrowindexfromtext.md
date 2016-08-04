<lowercasetitle/>

This function returns the GridList row index from the specified text.

Syntax
------

``` lua
int getGridListRowIndexFromText (element gridList, string text, int columnIndex)
```

### Required arguments

-   **gridList**: The grid list element.
-   **text**: The text that you want to retrieve his index.
-   **columnIndex**: The ID of the column.

### Return

Returns the row index (0 for the first element, 1 for the second, etc...), or false if the text doesn't exist.

Code
----

<section name="Client" class="client" show="true">
``` lua
function getGridListRowIndexFromText(gridList, text, column)
  for i=0, guiGridListGetRowCount(gridList)-1 do
    if (guiGridListGetItemText(gridList, i, column) == text) then
      return i
    end
     end
   return false
end
```

</section>
Example
-------

<section name="Example" class="client" show="true">
``` lua
local fruits = {"Apple","Banana","Orange","Melon","Pear"}

addEventHandler("onClientResourceStart", resourceRoot,
function ()
    fruitsList = guiCreateGridList(0.80, 0.10, 0.15, 0.60, true)
    local column = guiGridListAddColumn(fruitsList, "Fruits", 0.85)
    if (column) then
      for i, v in ipairs(fruits) do
        local row = guiGridListAddRow(fruitsList)
            guiGridListSetItemText(fruitsList, row, column, tostring(v), false, false)
        end
    end
end)
 
 
function getIndex()
  local index = getGridListRowIndexFromText(fruitsList,"Orange",1)
    if index then 
      outputChatBox("Row index: "..index,255,0,0)
    end 
end 
addCommandHandler("find",getIndex)
```

</section>
Author: Walid

See Also
--------
