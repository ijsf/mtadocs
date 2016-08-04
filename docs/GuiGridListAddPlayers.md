This function add all **online** players to a **grid list**.

Syntax
------

``` lua
bool guiGridListAddPlayers ( element gridList, int columnIndex, bool section, bool number )
```

### Required Arguments

-   **gridList**: The grid list element
-   **columnIndex**: Column ID
-   **section**: Determines if the item is a section
-   **number**: Tells whether the text item is a number value or not (used for sorting)

### Returns

Return all players in a **grid list**, false otherwise.

Code
----

<section name="Client" class="client" show="true">
``` lua
function guiGridListAddPlayers( GridList, Column, Section, Number )
    if( getElementType( GridList ) == "gui-gridlist" ) then
    assert( tonumber( Column ), "Bad argument @ 'guiGridListAddPlayers' [Expected number at argument 2, got " .. tostring(Column) .. "]" )
        if( Section == false or Section == true ) then
            if( Number == false or Number == true ) then
                for _, player in ipairs( getElementsByType('player') ) do
                    guiGridListClear( GridList )
                        local Row = guiGridListAddRow( GridList )
                        guiGridListSetItemText( GridList, Row, Column, getPlayerName(player), Section, Number )
                        end 
                    else
                    error("Bad argument @ 'guiGridListAddPlayers' [Expected boolean at argument 4, got " .. tostring(Number) .. "]")
                end
            else
            error("Bad argument @ 'guiGridListAddPlayers' [Expected boolean at argument 3, got " .. tostring(Section) .. "]")
        end
    end
end
```

</section>
Example
-------

This example add all **online players** in the server to a **grid list**

<section name="Example" class="client" show="true">
``` lua
-- Grid list 
    local screenW, screenH = guiGetScreenSize()
    Main_GridList = guiCreateGridList((screenW - 233) / 2, (screenH - 357) / 2, 233, 357, false)
    guiGridListAddColumn(Main_GridList, "Players", 0.9)
    guiSetVisible( Main_GridList, false )

-- For show Grid List
bindKey( "F10", "down", function( )
    guiSetVisible( Main_GridList, not guiGetVisible( Main_GridList ) )
    showCursor( not isCursorShowing( ) )
end )

-- This command add all players to a grid list
addCommandHandler( "addPlayers", function( )
    guiGridListAddPlayers( Main_GridList, 1, false, false )
end )
```

</section>
**Author**: MR.GRAND

**Hint**: This function can be useful, Shortcut way Add to the grid list of players.

See Also
--------
