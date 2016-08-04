This function returns the index of the selected combobox item.

Syntax
------

``` lua
int guiComboBoxGetSelected ( element comboBox )
```

### Required Arguments

-   **comboBox:** the combobox you want to know the selected item index of

### Returns

Returns the index of the selected item if the specified combobox is valid and has a selected item, *-1* if no item is selected, *false* or *nil* otherwise.

Example
-------

This example outputs selected item's text and ID to the chat.

``` lua
addCommandHandler("getSelected",
function (command)

local item = guiComboBoxGetSelected(comboBox)
local text = guiComboBoxGetItemText(comboBox, item)

outputChatBox("Currently selected item with ID: " .. tostring(item) .. " and with text: " .. text)

end)
```

See Also
--------
