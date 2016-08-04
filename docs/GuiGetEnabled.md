This function determines if a GUI element is enabled.

Syntax
------

``` lua
bool guiGetEnabled ( element guiElement )
```

### Required Arguments

-   **guiElement:** the GUI element to be checked.

### Returns

Returns *true* if the element is enabled, *false* otherwise.

Example
-------

<section name="Client" class="client" show="true">
``` lua
function ChangeMyButtonEnabled ( )        
        if ( guiGetEnabled ( MyButton ) == true ) then -- check if the element is enabled           
                guiSetEnabled ( MyButton, false ) -- if it is, we disable it
        else              
                guiSetEnabled ( MyButton, true ) -- if not, we make it enabled
        end
end

MyGuiWindow = guiCreateWindow(254,206,478,306,"Awesome Gui Window",false) -- Your gui window
MyButton = guiCreateButton(0.477,0.8268,0.1946,0.0784,"Hello World!",true,MyGuiWindow) -- Creates a button in your gui window
```

</section>
See Also
--------
