This function selects (ticks) or unselects a checkbox.

Syntax
------

``` lua
bool guiCheckBoxSetSelected ( element theCheckbox, bool state )
```

### Required Arguments

-   **theCheckbox:** The GUI element in which you wish to change the selection state of
-   **state:** The state of the checkbox, where *true* indicates selected, and *false* indicates unselected.

### Returns

Returns *true* if the checkbox's selection state was successfully set, *false* otherwise.

Example
-------

This example creates 2 checkboxes and sets one of them selected then checks if the first one is selected and if it is then the second one would be set selected.

``` lua
checkedBox = guiCreateCheckBox(20,30,150,20,"Checked checkbox",true,false)
uncheckedBox = guiCreateCheckBox(20,30,150,20,"UnChecked checkbox",false,false)

if(guiCheckBoxGetSelected(checkedBox))then
    guiCheckBoxSetSelected(uncheckedBox,true)
else
    guiCheckBoxSetSelected(checkedBox,true)
end
```

See Also
--------
