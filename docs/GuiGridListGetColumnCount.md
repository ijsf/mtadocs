This allows you to get the count of existing columns in a gridlist.

Syntax
------

``` lua
int guiGridListGetColumnCount ( element gridList )
```

### Required Arguments

-   **gridList:** The grid list you want to add a column to

### Returns

Returns an integer with the amount of columns in the gridlist, false otherwise.

Example
-------

This example outputs number of columns in gridList to chatBox when player uses command *getColumns*.

``` lua
addCommandHandler("getColumns",
function(command)

local columns = guiGridListGetColumnCount(theGridList)

if columns < 1 then
    outputChatBox("There are no columns.")
elseif columns >= 1 then
    outputChatBox("There are " .. tostring(columns) .. " columns.")
else
    outputChatBox("Unable to get number of columns.")
    
end 
end)
```

See Also
--------
