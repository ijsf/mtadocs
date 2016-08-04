This function changes the visibility state of a GUI element.

Syntax
------

``` lua
bool guiSetVisible ( element guiElement, bool state )
```

### Required Arguments

-   **guiElement:** the GUI element whose visibility is to be changed
-   **state:** the new visibility state

### Returns

Returns *true* if the element's visibility could be changed, *false* otherwise.

Example
-------

This example creates a gui window and changes its visibility every 2 seconds, infinite times.

``` lua
function changeVisibility ( )
        -- we check if the gui element is visible
        guiSetVisible (myWindow, not guiGetVisible ( myWindow ) )
end

--Create a gui window called 'myWindow'
myWindow = guiCreateWindow ( 0.3, 0.3, 0.5, 0.60, "GUI window title", true )
--Set a timer to change the window's visibility every 2 seconds, infinite times
setTimer ( changeVisibility, 2000, 0 )
```

This example creates a gui window with yes and no buttons and make it visible/invisible with the bindkey 'x'.

<section name="Client" class="client" show="true">
``` lua
newgui = { button = {}, wind= {} }

addEventHandler("onClientResourceStart", resourceRoot,
    
function()
newgui.wind[1] = guiCreateWindow(434, 304, 280, 123, "New Window", false)
guiWindowSetSizable(newgui.wind[1], false)
newgui.button[1] = guiCreateButton(35, 46, 87, 40, "yes", false, newgui.wind[1])
newgui.button[2] = guiCreateButton(166, 49, 92, 37, "no", false, newgui.wind[1])    
    end)

bindKey ( "x", "down", function ( )
        local state = ( not guiGetVisible ( newgui.wind[1] ) )
        guiSetVisible ( newgui.wind[1], state )
        showCursor ( state )
    end
)
```

</section>
See Also
--------
