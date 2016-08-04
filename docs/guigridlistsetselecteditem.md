This function selects an item from a gridlist. If you wish to deselect whatever item is selected, pass *0* as both the *rowIndex* and *columnIndex* arguments.

Syntax
------

``` lua
bool guiGridListSetSelectedItem ( element gridList, int rowIndex, int columnIndex [, bool bReset = true ] )
```

### Required Arguments

-   **gridList:** the grid list you want to select an item from
-   **rowIndex:** the row you want to select (index 0 is the first row)
-   **columnIndex:** the column you want to select (index 1 is the first column)

### Returns

Returns *true* if the passed arguments are correct and the item has been selected, *false* otherwise.

Example
-------

``` lua
guiGridListSetSelectedItem ( spawnScreenGridList, 0, 0) -- resets selection to zero
```

See Also
--------
