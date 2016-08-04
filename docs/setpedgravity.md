This function sets the gravity level of a ped.

Syntax
------

``` lua
bool setPedGravity ( ped thePed, float gravity )
```

### Required Arguments

-   **thePed**: The ped whose gravity to change.
-   **level**: The level of gravity (default is 0.008).

### Returns

Returns *true* if the gravity was successfully set, *false* otherwise

Example
-------

This example allows the user to type a command to change their gravity:

``` lua
function consoleSetPlayerGravity ( thePlayer, commandName, level )
    if thePlayer and level then
        local success = setPedGravity ( thePlayer, tonumber ( level ) )  -- Set the gravity
        if not success then                           -- Check if setPlayerGravity was false (not successful)
            outputConsole( "Failed to set ped gravity", thePlayer )  -- If success is false, meaning gravity could not be set, this message will show
        end
    end
end
addCommandHandler ( "setplayergravity", consoleSetPlayerGravity )
```

See Also
--------

[ru:setPedGravity](/docs/ru:setpedgravity.md "wikilink")
