This event is fired when the user double clicks a GUI element. Doesn't work with buttons.

Parameters
----------

``` lua
string button, string state, int absoluteX, int absoluteY
```

-   **button:** the name of the mouse button that the GUI element was double clicked with.
-   **state:** the state of the mouse button. “down” or “up”.
-   **absoluteX:** the X position of the mouse cursor, in pixels, measured from the left side of the screen.
-   **absoluteY:** the Y position of the mouse cursor, in pixels, measured from the top of the screen.

Source
------

The source of this event is the GUI element that was double clicked.

Example
-------

This example displays in chatbox name of double-clicked player in a gridlist.

``` lua
addEventHandler( "onClientResourceStart", getResourceRootElement( ),
    function ( )
        gridList = guiCreateGridList( 10, 200, 100, 50, false ) -- create a gridlist
        local col = guiGridListAddColumn( gridList, "Players", .9 ) -- add "Players" column

        local players = getElementsByType( "player" )
        for i, plr in pairs( players ) do -- loop through the table of players
            local row = guiGridListAddRow( gridList ); -- add row for player
            guiGridListSetItemText( gridList, row, col, getPlayerName( plr ), false, false ) -- change the text of the added row
        end

        addEventHandler( "onClientGUIDoubleClick", gridList, doubleClickedName, false )
    end
);

function doubleClickedName( )
    local selectedRow, selectedCol = guiGridListGetSelectedItem( gridList ); -- get double clicked item in the gridlist
    local playerName = guiGridListGetItemText( gridList, selectedRow, selectedCol ) -- get its text
    outputChatBox( "You double-clicked: " .. playerName ) -- display the text taken from gridlist
end
```

[pl:onClientGUIDoubleClick](/pl:onClientGUIDoubleClick.md "wikilink")

See Also
--------

### GUI events

### Client event functions
