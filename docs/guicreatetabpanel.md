This function creates a Tab Panel, which acts as a template to create Tabs upon.

Syntax
------

``` lua
element guiCreateTabPanel ( float x, float y, float width, float height, bool relative, [element parent = nil ] )
```

### Required Arguments

[frame|Example GUI tab panel with two tabs.](/docs/Image:gui-tabpanelandtab.png.md "wikilink")

-   **x:** A float of the 2D x position of the GUI tab panel on a player's screen. This is affected by the *relative* argument.
-   **y:** A float of the 2D y position of the GUI tab panel on a player's screen. This is affected by the *relative* argument.
-   **width:** A float of the width of the GUI tab panel. This is affected by the *relative* argument.
-   **height:** A float of the height of the GUI tab panel. This is affected by the *relative* argument.
-   **relative:** This is whether sizes and positioning are relative. If this is *true*, then all x,y,width,height floats must be between 0 and 1, representing sizes relative to the parent.

### Optional Arguments

-   **parent:** This is the parent that the tab panel is attached to. If the *relative* argument is true, sizes and positioning will be made relative to this parent. If the *relative* argument is false, positioning will be the number of offset pixels from the parent's origin. If no parent is passed, the parent will become the screen - causing positioning and sizing according to screen positioning.

### Returns

Returns a GUI tab panel element if successful, *false* otherwise.

Example
-------

This example creates a information window and adds two tabs to a “tabPanel” tabpanel, and adds some other gui elements to it.

``` lua
local myWindow = guiCreateWindow ( 0, 0, 0.5, 0.4, "Information", true )--create a window which has "Information" in the title bar.
local tabPanel = guiCreateTabPanel ( 0, 0.1, 1, 1, true, myWindow ) --create a tab panel which fills the whole window
local tabMap = guiCreateTab( "Map Information", tabPanel ) -- create a tab named "Map Information" on 'tabPanel'
local tabHelp = guiCreateTab( "Help", tabPanel ) -- create another tab named "Help" on 'tabPanel'

-- adds a label (text) to each tab
guiCreateLabel(0.02,0.04,0.94,0.2,"This is information about the current map",true,tabMap)
guiCreateLabel(0.02,0.04,0.94,0.92,"This is help text.",true,tabHelp)
```

See Also
--------
