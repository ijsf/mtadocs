This function allows you to set or remove read-only status for a GUI memo. If read-only is set to *true*, the contents are not editable.

Syntax
------

``` lua
bool guiMemoSetReadOnly ( gui-memo theMemo, bool status )
```

### Required Arguments

-   **theMemo:** The memo to change read-only status of.
-   **status:** A boolean value indicating whether read-only is to be enabled or disabled.

### Returns

Returns *true* if the status was successfully changed, *false* otherwise.

Example
-------

``` lua
addEventHandler( "onClientResourceStart", getResourceRootElement( getThisResource( ) ), -- only execute the code when this resource restarts
    function( )
        memo = guiCreateMemo( 0.4, 0.4, 0.2, 0.2, "This is a memo.", true ) -- create a relative memo GUI element
        guiMemoSetReadOnly( memo, true ) -- make it read only, so players won't be able to edit it in-game
    end
)
```

See Also
--------
