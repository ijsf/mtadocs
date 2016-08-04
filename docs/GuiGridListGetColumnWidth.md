This allows you to get the width of an existing column in a gridlist.

Syntax
------

``` lua
bool guiGridListGetColumnWidth ( element gridList, int columnIndex, bool relative )
```

### Required Arguments

-   **gridList:** The grid list you want to add a column to
-   **columnIndex:** Column ID of the Get size
-   **relative:** A boolean defining whether **width** measurements will be relative to the Gridlist size, or absolute pixels.

### Returns

Returns *true* if the gridlist column width was successfully set, *false* if bad arguments were given.

Example
-------

``` lua
grid = guiCreateGridList(313, 354, 162, 100, false)
c = guiGridListAddColumn(grid, "test",0.5)

addCommandHandler("With",function()
With = guiGridListGetColumnWidth(grid ,c, true)
outputChatBox("Column Width = "..With)
end
)
```

See Also
--------
