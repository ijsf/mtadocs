This function changes the text of a combobox item.

Syntax
------

``` lua
bool guiComboBoxSetItemText ( element comboBox, int itemId, string text )
```

### Required Arguments

-   **comboBox:** The combobox containing the item you're interested in
-   **itemId:** The index of the item
-   **text:** The text you want to put in (does NOT accept numbers, use tostring() for that)

### Returns

Returns *true* if the text was set successfully, *false* otherwise.

Example
-------

This changes the text of the selected item using command *setText*.

``` lua
addCommandHandler("setText",
function(cmd, text)

local item = guiComboBoxGetSelected(comboBox)
guiComboBoxSetItemText(comboBox, item, text)

end)
```

See Also
--------
