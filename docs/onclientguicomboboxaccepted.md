This event is called when a ComboBox get accepted

Parameters
----------

``` lua
element ComboBox
```

-   **ComboBox:** the ComboBox that got accepted.

Example
-------

This example will set the memo text to the selected combo box item text

``` lua
Combo = guiCreateComboBox ( 0.20, 0.03, 0.25, 0.30, "Example", true )
Memo = guiCreateMemo( 10, 50, 500, 150, "", false)
addEventHandler ( "onClientGUIComboBoxAccepted", guiRoot,
    function ( comboBox )
        if ( comboBox == Combo ) then
            local item = guiComboBoxGetSelected ( Combo )
            local text = tostring ( guiComboBoxGetItemText ( Combo , item ) )
            if ( text ~= "" ) then
                 guiSetText ( Memo , text )
            end
        end
    end
)
```

See Also
--------

### GUI events

### Client event functions
