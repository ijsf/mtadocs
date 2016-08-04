This function enables/disables a GUI element. A disabled GUI element can't be used, gets a gray aspect and doesn't receive any events.

Syntax
------

``` lua
bool guiSetEnabled ( element guiElement, bool enabled )
```

### Required Arguments

-   **guiElement:** the GUI element you wish to enable or disable
-   **enabled:** the new state

### Returns

If the function succeeds it returns *true*, if it fails it returns *false*.

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
