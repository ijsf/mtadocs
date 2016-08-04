This function is used to get the column title of a gridlist column.

Syntax
------

``` lua
string guiGridListGetColumnTitle( element guiGridlist, int columnIndex )
```

### Required Arguments

-   **guiGridlist**: The grid list you want to get the column title from
-   **columnIndex**: Column ID

### Returns

Returns a string containing the column title, or *false* otherwise.

Requirements
------------

Example
-------

<section name="Client" class="client" show="true">
``` lua

local theList = guiCreateGridList(0.80, 0.10, 0.15, 0.60, true) -- Create the grid list
local column = guiGridListAddColumn(theList, "New column", 0.9) -- Create a new column in the grid list
  
function GetColumnTitle()
  if column then 
    local ColumnTitle = guiGridListGetColumnTitle(theList,column) 
    outputChatBox("The Column Title Is: "..ColumnTitle, 0, 255, 0)--Get The column title in the chat
  end 
end
addCommandHandler("GetTitle", GetColumnTitle)
```

</section>
See Also
--------
