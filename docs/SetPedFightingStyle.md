Changes a ped's fighting style. Most styles only change the 'special attack' which is done using the Aim and Enter keys.

Syntax
------

``` lua
bool setPedFightingStyle ( ped thePed, int style )
```

### Required Arguments

-   **thePed:** The ped whose fighting style to change.
-   **style:** The fighting style ID to apply.

### Returns

Returns *true* in case of success, *false* otherwise.

Example
-------

This example sets the player's fighting style to the desired style when he types “setstyle” followed by a number from 4 to 16 in console.

``` lua
function consoleSetFightingStyle ( thePlayer, commandName, id )
    if thePlayer and id then                                                     -- If player and ID are specified
        local status = setPedFightingStyle ( thePlayer, tonumber(id) )       -- set the fighting style
        if not status then                                                   -- if that failed
            outputConsole ( "Failed to set fighting style.", thePlayer ) -- show a message
        end
    end
end
addCommandHandler ( "setstyle",  consoleSetFightingStyle )
```

See Also
--------

[ru:setPedFightingStyle](/ru:setPedFightingStyle.md "wikilink")
