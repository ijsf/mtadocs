This function deletes a tab from a tab panel.

Syntax
------

``` lua
bool guiDeleteTab ( element tabToDelete, element tabPanel )
```

### Required Arguments

-   **tabToDelete:** This is an element representing the tab that you want to delete.
-   **tabPanel:** This is the [tab panel](/docs/guiCreateTabPanel.md "wikilink") parent that the tab is attached to.

### Returns

Returns *true* the tab was successfully deleted, *false* otherwise.

Example
-------

This example removes a tab panel if a user LeftCtrl+Clicks a tab panel.

``` lua
function deleteTabOnClick ()
    if ( getKeyState ( "lctrl" ) == true ) and ( getElementType( source ) == "gui-tab" ) then    -- if the user is holding down left control
        guiDeleteTab ( source, getElementParent(source) )                -- delete the tab. No need to check if it was actually a tab that was clicked, as this function doesn't work on other controls anyway
    end
end
addEventHandler ( "onClientGUIClick", getRootElement(), deleteTabOnClick  )    -- add an event handler for clicks
```

See Also
--------
