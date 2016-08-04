This function creates a grid list GUI element. These are menu's which are designed in lists and can have multiple columns. A good example of a gridlist element can be found in MTA's settings box, under *Controls*.

Syntax
------

``` lua
element guiCreateGridList ( float x, float y, float width, float height, bool relative, [ element parent = nil ] )
```

### Required Arguments

[frame|Example GUI gridlist.](/Image:Gui-gridlist.png.md "wikilink")

-   **x:** A float of the 2D x position of the GUI gridlist on a player's screen. This is affected by the *relative* argument.
-   **y:** A float of the 2D y position of the GUI gridlist on a player's screen. This is affected by the *relative* argument.
-   **width:** A float of the width of the GUI gridlist. This is affected by the *relative* argument.
-   **height:** A float of the height of the GUI gridlist. This is affected by the *relative* argument.
-   **relative:** This is whether sizes and positioning are relative. If this is *true*, then all x,y,width,height floats must be between 0 and 1, representing sizes relative to the parent.

### Optional Arguments

-   **parent:** This is the parent that the gui gridlist is attached to. If the *relative* argument is true, sizes and positioning will be made relative to this parent. If the *relative* argument is false, positioning will be the number of offset pixels from the parent's origin. If no parent is passed, the parent will become the screen - causing positioning and sizing according to screen positioning.

### Returns

Returns an element of the created gridlist if it was successfully created, false otherwise.

Example
-------

**Example 1:** This example creates a player list on the right of the screen and fills it

``` lua
function createPlayerList ()
    --Create the grid list element
    local playerList = guiCreateGridList ( 0.80, 0.10, 0.15, 0.60, true )
    --Create a players column in the list
    local column = guiGridListAddColumn( playerList, "Player", 0.85 )
    if ( column ) then --If the column has been created, fill it with players
        for id, player in ipairs(getElementsByType("player")) do
            local row = guiGridListAddRow ( playerList )
            guiGridListSetItemText ( playerList, row, column, getPlayerName ( player ), false, false )
        end
    end
end
```

**Example 2:** This example creates a weapon selection screen, complete with a window, gridlist and a button. Users can select a shotgun or a machine gun. The window is not movable or sizable.

``` lua
--Setup some tables
shotguns = {
"chrome",
"sawn-off",
"combat" }

machineGun = {
"m4",
"ak-47"
 }

function setupWeaponSelection ()
        ---Create a window for our spawnscreen, with the title "Select your weaposn".
        spawnScreenMenu = guiCreateWindow ( 0.15, 0.33, 0.7, 0.34, "Select your weapons", true )
        --create an OK button to allow the user to confirm their seclections, and attach it to the confirmSelection funnction
        spawnScreenOKButton = guiCreateButton ( 0.4, 0.85, 0.20, 0.15, "OK", true, spawnScreenMenu )
        --ensure the user doesnt move or resize our spawnscreen.
        guiWindowSetMovable ( spawnScreenMenu, false )
        guiWindowSetSizable ( spawnScreenMenu, false )
        --create our gridlist, which fills up most of the window.
        spawnScreenGridList = guiCreateGridList ( 0, 0.1, 1, 0.9, true, spawnScreenMenu )
        guiGridListSetSelectionMode ( spawnScreenGridList, 2 )--ensure the selection mode is one per column
        --Since we have 2 sets of weapons, create one for shotguns and one for machine guns
        guiGridListAddColumn ( spawnScreenGridList, "Shotguns", 0.3 )
        guiGridListAddColumn ( spawnScreenGridList, "Machine guns", 0.3 )
        -- next, we loop through our handguns table to add handgun items to the gridlist
        for key,weaponName in pairs(shotguns) do
                --add a new row to our gridlist each time
                local row = guiGridListAddRow ( spawnScreenGridList ) --get our new row
                --next, we set that rows text to the weapon name.  Column is 1 since the "Shotguns" column was created first.
                guiGridListSetItemText ( spawnScreenGridList, row, 1, weaponName, false, false )
        end
        --we repeat the process for other weapon lists, changing the column number
        row = 0
        for key,weaponName in pairs(machineGun) do
                --we dont bother creating new rows, since we already have done that
                --next, we set that rows text to the weapon name.  Column is 2 since the "Machine guns" column was created second.
                guiGridListSetItemText ( spawnScreenGridList, row, 2, weaponName, false, false )
                row = row + 1 --increase the row number
        end
end
addEventHandler ( "onClientResourceStart", getResourceRootElement(), setupWeaponSelection )
```

See Also
--------
