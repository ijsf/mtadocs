This function adjusts your combobox to the correct height. Small comboboxes do not show a list when clicking; their list height is based on element height too.

Syntax
------

``` lua
string guiComboBoxAdjustHeight ( element combobox, int itemcount )
```

### Required Arguments

-   **combobox**: The gui-combobox element.
-   **itemcount**: The amount of listitems your combobox has.

### Returns

Returns true if there were no errors, false otherwise.

Code
----

<section name="Clientside script" class="client" show="true">
``` lua
function guiComboBoxAdjustHeight ( combobox, itemcount )
    if getElementType ( combobox ) ~= "gui-combobox" or type ( itemcount ) ~= "number" then error ( "Invalid arguments @ 'guiComboBoxAdjustHeight'", 2 ) end
    local width = guiGetSize ( combobox, false )
    return guiSetSize ( combobox, width, ( itemcount * 20 ) + 20, false )
end
```

</section>
Example
-------

No example &gt;:(

See Also
--------
