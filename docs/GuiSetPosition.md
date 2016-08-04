This function sets the position of a GUI element.

Syntax
------

``` lua
bool guiSetPosition ( element theElement, float x, float y, bool relative )
```

### Required Arguments

-   **theElement:** The GUI element to change position for
-   **x:** Position over the X axis
-   **y:** Position over the Y axis
-   **relative:** Bool that indicates if the x/y positions are relative to the screen size

### Returns

Returns *true* if the position has been successfully set, *false* otherwise.

Example
-------

This example creates a label. When an element is clicked, the label displays in the position of the element telling you what kind of element you have clicked. It hides after 5 seconds.

``` lua
--create an empty label
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
