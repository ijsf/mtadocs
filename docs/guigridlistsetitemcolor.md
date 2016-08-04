This function changes the color of a gridlist item.

Syntax
------

``` lua
bool guiGridListSetItemColor ( element gridList, int rowIndex, int columnIndex, int red, int green, int blue [, int alpha = 255 ] )
```

### Required Arguments

-   **gridList:** The grid list element
-   **rowIndex:** Row ID
-   **columnIndex:** Column ID
-   **red:** The amount of red in the color (0-255)
-   **green:** The amount of green in the color (0-255)
-   **blue:** The amount of blue in the color (0-255)

### Optional Arguments

-   **alpha:** The amount of alpha in the color (0-255).

### Returns

Returns *true* if the item color was set successfully, *false* otherwise.

Example
-------

<section name="Client" class="client" show="true">
This example creates a player list on the right of the screen and fills it with players online and sets the grid list item color according to their nametag color.

``` lua
function createPlayerList ( )
    --Create the grid list element
    local playerList = guiCreateGridList ( 0.80, 0.10, 0.15, 0.60, true )
    --Create a players column in the list
    local column = guiGridListAddColumn( playerList, "Player", 0.85 )
    if ( column ) then --If the column has been created, fill it with players
        for id, player in ipairs ( getElementsByType ( "player" ) ) do
            local row = guiGridListAddRow ( playerList )
            local r, g, b = getPlayerNametagColor ( player ) -- We get the player nametag color.
            guiGridListSetItemText ( playerList, row, column, getPlayerName ( player ), false, false )
            guiGridListSetItemColor ( playerList, row, column, r, g, b ) -- We set the grid list item color to the returned values of getPlayerNametagColor.
        end
    end
end
addEventHandler ( "onClientResourceStart", resourceRoot, createPlayerList )
```

</section>
See Also
--------
