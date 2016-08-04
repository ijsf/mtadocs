This function gets the value of a specific CEGUI property of a GUI element. For a list of properties and their meaning, see the [CEGUI properties wiki page](http://www.cegui.org.uk/wiki/index.php/SetProperty_(WindowsLook)).

Syntax
------

``` lua
string guiGetProperty ( element guiElement, string property )
```

### Required Arguments

-   **guiElement:** the GUI element you wish to get a property of.
-   **property:** the name of of property you want the value of.

### Returns

If the function succeeds, it returns a string with the value of the property. If it fails, it returns *false*.

Example
-------

This example creates a button when the resource starts and defines a console command that toggles it between enabled (clickable) and disabled (not clickable).

``` lua
addEventHandler("onClientResourceStart", getResourceRootElement(),
    function()
        button = guiCreateButton(20, 200, 150, 30, "Test", false)
    end
)

addCommandHandler("togglebtn",
    function()
        local currentState = guiGetProperty(button, "Disabled")
        if currentState == "False" then
            guiSetProperty(button, "Disabled", "True")
        else
            guiSetProperty(button, "Disabled", "False")
        end
    end
)
```

See Also
--------
