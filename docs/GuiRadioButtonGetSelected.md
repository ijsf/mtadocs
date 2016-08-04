This function gets a radio button's selection state.

Syntax
------

``` lua
bool guiRadioButtonGetSelected( element guiRadioButton )
```

### Required Arguments

-   **guiRadioButton:** The radio button you wish to retrieve the selection state of.

### Returns

Returns *true* if the radio button is selected, *false* if it is not.

Example
-------

This example creates a radio button then checks if one is selected and if it is, then it's output the title and sets the next radio button selected. (TESTED!)

``` lua
hi = guiCreateRadioButton(243,204,36,16,"Hi",false)
guiRadioButtonSetSelected(hi,true)
bye = guiCreateRadioButton(243,224,41,16,"Bye",false)

if(guiRadioButtonGetSelected(hi))then
    outputChatBox("Hi "..getPlayerName(localPlayer))
    guiRadioButtonSetSelected(bye,true)
else
    outputChatBox("Bye "..getPlayerName(localPlayer))
    guiRadioButtonSetSelected(hi,true)
end
```

See Also
--------
