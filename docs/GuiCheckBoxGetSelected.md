This function gets a checkbox's selection state.

Syntax
------

``` lua
bool guiCheckBoxGetSelected ( element theCheckbox )
```

### Required Arguments

-   **theCheckbox :** The checkbox you wish to retrieve the selection state of.

### Returns

Returns *true* if the checkbox is selected, *false* if it is not.

Example
-------

This example makes a different beep based on the state when any checkbox has been clicked.

``` lua
function checkboxBleepWhenClicked()
    if ( getElementType(source) == "gui-checkbox" ) then -- Is the element clicked a checkbox?
        if ( guiCheckBoxGetSelected(source) ) then
            playSoundFrontEnd(1) -- If the checkbox is selected play sound 1.
        else
            playSoundFrontEnd(2) -- If the checkbox isn't selected play sound 2.
        end
    end
end
addEventHandler("onClientGUIClick", root, checkboxBleepWhenClicked, false)
```

See Also
--------
