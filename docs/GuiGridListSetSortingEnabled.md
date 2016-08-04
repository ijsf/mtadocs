This function allows the disabling or enabling of *sorting* within a gridlist. Sorting is achieved by clicking a column header. Gridlist items will be sorted according to the clicked column. By default, gridlists have sorting enabled. This function will allow you to toggle this.

Syntax
------

``` lua
bool guiGridListSetSortingEnabled ( element guiGridlist, bool enabled )
```

### Required Arguments

-   **guiGridlist:** The GUI gridlist you wish to toggle the sorting of.
-   **enabled:** A boolean representing whether the sorting is enabled, or disabled.

### Returns

Returns *true* if sorting was successfully toggled., *false* otherwise.

Example
-------

**Example 1:** This example creates a gridlist, fills it with players connected to the server and disables the sorting for that gridlist

``` lua
function createGridList ()
    --Create the grid list element
    local newGridlist = guiCreateGridList ( 0.50, 0.50, 0.20, 0.30, true )
    --Create a new grid list
        local column = guiGridListAddColumn( newGridlist, "Players", 0.85 )
    if ( column ) then --If the column has been created, fill it with players
        for id, player in ipairs(getElementsByType("player")) do
            local row = guiGridListAddRow ( newGridlist )
            guiGridListSetItemText ( newGridlist, row, column, getPlayerName ( player ), false, false )
        end
    end
    guiGridListSetSortingEnabled ( newGridlist, false )
        --Disable sorting for the gridlist
end
```

See Also
--------
