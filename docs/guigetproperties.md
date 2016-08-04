This function gets a list of the CEGUI property names and values of a GUI element. To find out what the different properties mean, check out the [CEGUI properties wiki page](http://www.cegui.org.uk/wiki/index.php/SetProperty_(WindowsLook)).

Syntax
------

``` lua
table guiGetProperties ( element guiElement )
```

### Required Arguments

-   **guiElement:** the GUI element you wish to get the properties of.

### Returns

If the function succeeds, the return value is a table. Its keys are property names, the corresponding values are the values of the properties (both names and values are always strings). If the function fails, it returns *false*.

Example
-------

The following example code will create a button and lists its properties in the console if the /btn command is entered.

``` lua
addCommandHandler("btn",
    function()
        local btn = guiCreateButton(20, 200, 150, 30, "Test", false)
        local props = guiGetProperties(btn)
        for propName,propVal in pairs(props) do
            outputConsole(propName .. " = " .. propVal)
        end
    end
)
```

See Also
--------
