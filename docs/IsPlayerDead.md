This function checks if the specified [player](/docs/player.md "wikilink") is dead or not.

Syntax
------

``` lua
bool isPlayerDead ( player thePlayer )
```

### Required Arguments

-   **thePlayer**: A [player](/docs/player.md "wikilink") object referencing the specified player

### Returns

Returns *true* if the player is dead, *false* otherwise.

Example
-------

<section name="Server" class="server" show="true">
This example allows a player to use the command 'amidead' to see if they are dead or not.

``` lua
--Check if player is alive or dead and let them know in the chat box
function deathCheck ( thePlayer, commandName )
    if ( isPlayerDead ( thePlayer ) ) then
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
