[frame|Example GUI label.](/docs/Image:gui-label.png.md "wikilink")

<table>
<tr>
<td valign=top height=100>
This function is for creating a new GUI label. A label is simply a piece of text that cannot be edited by the user. If you would like to have a bigger text you'd have to change its font because font size is not supported.

</td>
</tr>
</table>
Syntax
------

``` lua
element guiCreateLabel ( float x, float y, float width, float height, string text, bool relative, [element parent = nil] )
```

### Required Arguments

-   **x:** A float of the 2D x position of the GUI label on a player's screen. This is affected by the *relative* argument.
-   **y:** A float of the 2D y position of the GUI label on a player's screen. This is affected by the *relative* argument.
-   **width:** A float of the width of the GUI label. This is affected by the *relative* argument.
-   **height:** A float of the height of the GUI label. This is affected by the *relative* argument.
-   **text:** A string of the text that will be displayed by the label.
-   **relative:** This is whether sizes and positioning are relative. If this is *true*, then all x,y,width,height floats must be between 0 and 1, representing sizes relative to the parent.

### Optional Arguments

-   **parent:** This is the parent that the gui label is attached to. If the *relative* argument is true, sizes and positioning will be made relative to this parent. If the *relative* argument is false, positioning will be the number of offset pixels from the parent's origin. If no parent is passed, the parent will become the screen - causing positioning and sizing according to screen positioning.

### Returns

Returns an [element](/docs/GUI_widgets.md "wikilink") of the created label if it was successfully created, false otherwise.

Example
-------

**Example 1:** This example creates a information window and adds two tabs to a “tabPanel” tabpanel, and adds some gui labels to each tab.

``` lua
local myWindow = guiCreateWindow ( 0, 0, 0.5, 0.4, "Information", true )--create a window which has "Information" in the title bar.
local tabPanel = guiCreateTabPanel ( 0, 0.1, 1, 1, true, myWindow ) --create a tab panel which fills the whole window
local tabMap = guiCreateTab( "Map Information", tabPanel ) -- create a tab named "Map Information" on 'tabPanel'
local tabHelp = guiCreateTab( "Help", tabPanel ) -- create another tab named "Help" on 'tabPanel'

-- adds a label (text) to each tab
guiCreateLabel(0.02,0.04,0.94,0.2,"This is information about the current map",true,tabMap)
guiCreateLabel(0.02,0.04,0.94,0.92,"This is help text.",true,tabHelp)
```

**Example 2:** This example creates a label. When an element is clicked, the label displays in the position of the element telling you what kind of element you have clicked. It hides after 5 seconds.

``` lua
local myLabel = guiCreateLabel  ( 0, 0, 1, 1, "", true )

function addLabelOnClick ( button, state, absoluteX, absoluteY, worldX, worldY, worldZ, clickedElement )
        --if an element was clicked on screen
        if ( clickedElement ) then
                --retreive the element type
                local elementType = getElementType ( clickedElement )
                --change the label text to that element type
                guiSetText ( myLabel, elementType )
                --and place it in the position of where the element is
                guiSetPosition ( myLabel, absoluteX, absoluteY, false )
                --hide the text by passing an empty string 5 seconds later
                setTimer ( guiSetText, 5000, 1, myLabel, "" )
        end
end
addEventHandler ( "onClientClick", getRootElement(), addLabelOnClick )
```

See Also
--------

[ru:guiCreateLabel](/docs/ru:guiCreateLabel.md "wikilink")
