Please use [setPedGravity](/setPedGravity.md "wikilink")

Description
-----------

This function sets the gravity level of a player.

Syntax
------

``` lua
setPlayerGravity ( player thePlayer, float level )
```

### Required Arguments

-   **thePlayer**: The player whose gravity to change.
-   **level**: The level of gravity ( default is <b>0.008</b> )

Example
-------

<section name="Server" class="server" show="true">
This example allows the user to type a command to change their gravity:

``` lua
function consoleSetPlayerGravity ( thePlayer, commandName, level )
    if ( thePlayer and level ) then
        local success = setPlayerGravity ( thePlayer, tonumber ( level ) )  -- Sets the gravity
        if (not success) then --Check if setPlayerGravity was false (not successful)
            outputConsole( "Failed to set player gravity", thePlayer )  -- If success is false, meaning gravity could not be set, this message will show
        end
    end
end
addCommandHandler ( "setplayergravity", consoleSetPlayerGravity )
```

</section>
See Also
--------
