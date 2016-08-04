Please use [setPedFightingStyle](/docs/setPedFightingStyle.md "wikilink")

Changes a player's fighting style, most only change the 'special attack' which is done using the Aim and Enter keys.

Syntax
------

``` lua
setPlayerFightingStyle ( player thePlayer, int style ) 
```

### Required Arguments

-   **thePlayer:** Tells the function to give the fighting style to a player
-   **style:** A whole integer specifying the style of fighting you want to give to the player

Example
-------

<section name="Server" class="server" show="true">
This example sets the player's fighting style to the desired style when he types “setstyle” followed by a number from 4 to 16 in console.

``` lua
function consoleSetFightingStyle ( thePlayer, commandName, id )
    if ( thePlayer and id ) then                                                 -- If player and ID are specified
        local status = setPlayerFightingStyle ( thePlayer, tonumber(id) )    -- set the fighting style
        if ( not status ) then                                               -- if that failed
            outputConsole ( "Failed to set fighting style.", thePlayer ) -- show a message
        end
    end
end
addCommandHandler ( "setstyle",  consoleSetFightingStyle )
```

</section>
See Also
--------
