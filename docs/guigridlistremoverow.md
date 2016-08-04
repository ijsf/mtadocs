This allows you to delete rows that exist in grid lists.

Syntax
------

``` lua
bool guiGridListRemoveRow ( element gridList, int rowIndex )
```

### Required Arguments

-   **gridList:** The grid list you want to remove a row from
-   **rowIndex:** The row ID which you want to remove

### Returns

Returns *true* if the grid list row was successfully removed, *false* otherwise.

Example
-------

In this example, when the script starts, a grid list with 1 column and 2 rows, which have text assigned to them. After 3 seconds, one row is randomly deleted.

``` lua
function deleteRow ()
        --Choose randomly which row to delete, output the
        --chosen row into the chat box, and delete the row
        randomDeletion = math.random ( 1, 2 )   
        if randomDeletion == 1 then
            outputChatBox ( "Removing row A" )
            guiGridListRemoveRow ( myGridList, rowA )
        elseif randomDeletion == 2 then    
            outputChatBox ( "Removing row B" )
            guiGridListRemoveRow ( myGridList, rowB )
        end
end


function clientsideResourceStart ()
    --Create a gridlist
        myGridList = guiCreateGridList ( 0.30, 0.10, 0.5, 0.60, true ) 
        --Create a column for myGridList to add rows into
        columnA = guiGridListAddColumn ( myGridList, "columnA Title", 0.25 ) 
    --Create 2 rows for ColumnA and set the text for them
        rowA = guiGridListAddRow ( myGridList )
    guiGridListSetItemText ( myGridList, rowA, columnA, "Hello", false, false )
    rowB = guiGridListAddRow ( myGridList )
    guiGridListSetItemText ( myGridList, rowB, columnA, "World!", false, false )
    --Trigger the function to delete a row 3 seconds after the script starts
        setTimer ( deleteRow, 3000, 1 )
end
addEventHandler ( "onClientResourceStart", resourceRoot, clientsideResourceStart )
```

See Also
--------
