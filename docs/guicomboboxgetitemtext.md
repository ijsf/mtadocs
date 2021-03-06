This function retrieves the text from a specific combobox item.

Syntax
------

``` lua
string guiComboBoxGetItemText ( element comboBox, int itemId )
```

### Required Arguments

-   **comboBox:** The combobox containing the item you're interested in
-   **itemId:** The index of the item

### Returns

Returns the text of the item if the arguments are right, *false* otherwise.

Example
-------

This outputs selected item's text to the chatbox.

``` lua
local item = guiComboBoxGetSelected(comboBox)
local text = guiComboBoxGetItemText(comboBox, item)

outputChatBox("You have selected: " .. text)
```

See Also
--------
