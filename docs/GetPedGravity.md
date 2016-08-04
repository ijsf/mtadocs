This function returns the current gravity for the specified [ped](/docs/ped.md "wikilink"). The default gravity is 0.008.

Syntax
------

``` lua
float getPedGravity ( ped thePed )
```

### Required Arguments

-   **thePed:** The [ped](/docs/ped.md "wikilink") whose gravity you want to check.

### Returns

Returns a [float](/docs/float.md "wikilink") indicating the ped's gravity, or *false* if the ped is invalid. Default value is 0.008.

Example
-------

This example outputs the gravity of the player who entered the 'showGravity' command.

``` lua
function showGravity ( thePlayer )
    local gravity = getPedGravity ( thePlayer )
    outputChatBox ( "Your gravity: " .. tostring(gravity), thePlayer )
end
addCommandHandler ( "showGravity", showGravity )
```

See Also
--------
