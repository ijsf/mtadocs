This function creates a combobox GUI element, which you can compare to a gridlist with a dropdown feature.

-   **NOTE:** The height of a combobox must be enough to fit the drop down menu, else the drop down won't appear. See [guiComboBoxAdjustHeight](/docs/guicomboboxadjustheight.md "wikilink") to give your combobox the correct height.

Syntax
------

``` lua
element guiCreateComboBox ( float x, float y, float width, float height, string caption, bool relative, [ element parent = nil ] )
```

### Required Arguments

[frame|Example GUI ComboBox.](/docs/image-gui-combobox.jpg.md "wikilink")

-   **x:** A float of the 2D x position of the GUI combobox on a player's screen. This is affected by the *relative* argument.
-   **y:** A float of the 2D y position of the GUI combobox on a player's screen. This is affected by the *relative* argument.
-   **width:** A float of the width of the GUI combobox. This is affected by the *relative* argument.
-   **height:** A float of the height of the GUI combobox. This is affected by the *relative* argument. Note: height must be enough to fit the drop down menu, else the drop down won't appear.
-   **caption:** A string for what the title of your combobox will be. This will be shown if no item is selected.
-   **relative:** This is whether sizes and positioning are relative. If this is *true*, then all x,y,width,height floats must be between 0 and 1, representing sizes relative to the parent.

### Optional Arguments

-   **parent:** This is the parent that the GUI combobox is attached to. If the *relative* argument is true, sizes and positioning will be made relative to this parent. If the *relative* argument is false, positioning will be the number of offset pixels from the parent's origin. If no parent is passed, the parent will become the screen - causing positioning and sizing according to screen positioning.

### Returns

Returns an element of the created combobox if it was successfully created, false otherwise.

Example
-------

This example creates a combo box in the center of the screen with all server vehicles on it.

``` lua
addEventHandler ("onClientResourceStart",resourceRoot,function()
    local screenWidth, screenHeight = guiGetScreenSize()
    local windowWidth, windowHeight = 200,100
    local left = screenWidth/2 - windowWidth/2
    local top = screenHeight/2 - windowHeight/2
    local vehiclesComboBox = guiCreateComboBox ( left, top, windowWidth,windowHeight, "Vehicle Names", false ) -- We create a combo box.
    for index, vehicle in ipairs ( getElementsByType ( "vehicle" ) ) do -- We loop through all vehicles.
        guiComboBoxAddItem ( vehiclesComboBox, getVehicleName ( vehicle ) ) -- We add the vehicle name to our combo box.
    end
end)
```

See Also
--------
