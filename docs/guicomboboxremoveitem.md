This function removes an item from a combobox.

Syntax
------

``` lua
bool guiComboBoxRemoveItem( element comboBox, int itemId )
```

### Required Arguments

-   **comboBox:** The combobox containing the item you're interested in
-   **itemId:** The index of the item to remove

### Returns

Returns *true* if the item was removes successfully, *false* otherwise.

Example
-------

This example removes selected item.

``` lua
addCommandHandler("remove",
function (command)

local item = guiComboBoxGetSelected(comboBox)
local text = guiComboBoxGetItemText(comboBox, item)
guiComboBoxRemoveItem(comboBox, item)
outputChatBox("Item with text " .. text .. " has been removed!")

end)
```

See Also
--------
