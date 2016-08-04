This function checks if the specified [ped](/docs/ped.md "wikilink") is dead or not.

Syntax
------

``` lua
bool isPedDead ( ped thePed )
```

### Required Arguments

-   **thePed**: the [ped](/docs/ped.md "wikilink") you want to check up on.

### Returns

Returns *true* if the ped is dead, *false* otherwise.

Example
-------

<section name="Server" class="server" show="true">
This example allows a player to use the command 'amidead' to see if they are dead or not.

``` lua
--Check if player is alive or dead and let them know in the chat box
function deathCheck ( thePlayer, commandName )
    if ( isPedDead ( thePlayer ) ) then
         outputChatBox ( "You're dead... prepare to become a zombie.", thePlayer )
    else
         outputChatBox ( "Count your lucky stars, you're alive.", thePlayer )
    end
end
addCommandHandler ( "amidead", deathCheck )
```

</section>
See Also
--------
