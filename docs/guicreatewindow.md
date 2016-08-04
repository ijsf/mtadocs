This function is for creating a new GUI window. This provides a base for other gui elements to be created within. However, windows do not have a parent and cannot be created in any GUI elements.

Syntax
------

``` lua
element guiCreateWindow ( float x, float y, float width, float height, string titleBarText, bool relative )
```

### Required Arguments

[frame|Example Window.](/docs/Image:gui-window.png.md "wikilink")

-   **x:** A float of the 2D x position of the GUI window on a player's screen. This is affected by the *relative* argument.
-   **y:** A float of the 2D y position of the GUI window on a player's screen. This is affected by the *relative* argument.
-   **width:** A float of the width of the GUI window. This is affected by the *relative* argument.
-   **height:** A float of the height of the GUI window. This is affected by the *relative* argument.
-   **titleBarText:** A string of the text that will be displayed in the title bar of the window.
-   **relative:** This is whether sizes and positioning are relative. If this is *true*, then all x,y,width,height floats must be between 0 and 1, representing sizes/positions as a fraction of the screen size. If *false*, then the size and co-ordinates are based on client's resolution, accessible using [guiGetScreenSize](/docs/guiGetScreenSize.md "wikilink").

### Returns

Returns a gui window element if it was created successfully, false otherwise.

Example
-------

**Example 1:** This example creates a information window and adds two tabs to a “tabPanel” tabpanel, and adds some other gui elements to it.

``` lua
local myWindow = guiCreateWindow ( 0, 0, 0.5, 0.4, "Information", true )  -- create a window which has "Information" in the title bar.
local tabPanel = guiCreateTabPanel ( 0, 0.1, 1, 1, true, myWindow )       -- create a tab panel which fills the whole window
local tabMap = guiCreateTab( "Map Information", tabPanel )                -- create a tab named "Map Information" on 'tabPanel'
local tabHelp = guiCreateTab( "Help", tabPanel )                          -- create another tab named "Help" on 'tabPanel'

-- adds a label (text) to each tab
guiCreateLabel(0.02, 0.04, 0.94, 0.2, "This is information about the current map", true, tabMap)
guiCreateLabel(0.02, 0.04, 0.94, 0.92, "This is help text.", true, tabHelp)
```

**Example 2:** This example creates a weapon selection screen, complete with a window, gridlist and a button. Users can select a shotgun or a machine gun. The window is not movable or sizable.

``` lua
--Setup some tables

shotguns = {
      "chrome",
      "sawn-off",
      "combat"
}

machineGun = {
      "m4",
      "ak-47"
}

function setupWeaponSelection ( theResource )
      -- getResourceRootElement(getThisResource()) at the bottom means it will only create the gui on this resource start
      -- Create a window for our spawnscreen, with the title "Select your weapons".
      spawnScreenMenu = guiCreateWindow ( 0.15, 0.33, 0.7, 0.34, "Select your weapons", true )
      -- create an OK button to allow the user to confirm their selections, and attach it to the confirmSelection function
      spawnScreenOKButton = guiCreateButton ( 0.4, 0.85, 0.20, 0.15, "OK", true, spawnScreenMenu )
      -- ensure the user can't move or resize our spawnscreen.
      guiWindowSetMovable ( spawnScreenMenu, false )
      guiWindowSetSizable ( spawnScreenMenu, false )
      -- create our gridlist, which fills up most of the window.
      spawnScreenGridList = guiCreateGridList ( 0, 0.1, 1, 0.9, true, spawnScreenMenu )
      guiGridListSetSelectionMode ( spawnScreenGridList, 2 ) -- ensure the selection mode is one per column
      -- Since we have 2 sets of weapons, create a column for shotguns and one for machine guns
      guiGridListAddColumn ( spawnScreenGridList, "Shotguns", 0.3 )
      guiGridListAddColumn ( spawnScreenGridList, "Machine guns", 0.3 )
      -- next, we loop through our handguns table to add handgun items to the gridlist
      for key,weaponName in pairs(shotguns) do
            -- add a new row to our gridlist each time
            local row = guiGridListAddRow ( spawnScreenGridList )
            -- next, we set that row's text to the weapon name. Column is 1 since the "Shotguns" column was created first.
            guiGridListSetItemText ( spawnScreenGridList, row, 1, weaponName, false, false )
      end
      -- we repeat the process for other weapon list, changing the column number
      row = 0
      for key,weaponName in pairs(machineGun) do
            -- we don't need to create new rows as that was done in the previous loop
            -- we just set the row's text to the weapon name. Column is 2 since the "Machine guns" column was created second.
            guiGridListSetItemText ( spawnScreenGridList, row, 2, weaponName, false, false )
            row = row + 1 -- increase the row number
      end
end
addEventHandler ( "onClientResourceStart", getResourceRootElement(getThisResource()), setupWeaponSelection )
```

See Also
--------

[ru:guiCreateWindow](/docs/ru:guiCreateWindow.md "wikilink")
