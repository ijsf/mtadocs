Adds an item to a combobox.

Syntax
------

``` lua
int guiComboBoxAddItem( element comboBox, string value )
```

### Required Arguments

-   **comboBox:** The combobox you want to add a row to
-   **value:** The text that the item will contain.

### Returns

Returns the item ID if it has been created, *false* otherwise.

Example
-------

This Example will add an item to comboBox when player use command *addItem* followed by the value of the item.

``` lua
addCommandHandler("addItem",
function (command, value)

guiComboBoxAddItem(comboBox, value)
outputChatBox("Item with text " .. value .. " has been added!")
 
end)
```

See Also
--------
