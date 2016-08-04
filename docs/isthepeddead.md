{{ Useful Function }}

This function checks if the specified [ped](/docs/ped.md "wikilink") is dead . '''NOTE: ''' There's a function called [isPedDead](/docs/ispeddead.md "wikilink") but it's server side . This function works on poth server and client side .

### Code

<section name="Server / Client" class="both" show="true">
``` lua
function isThePedDead( ped )
    if ped and isElement( ped ) and getElementType( ped ) == 'ped' then
        if getElementHealth( ped ) <= 0 then
            return true
        end
    end
    return false
end
```

</section>
### Syntax

``` lua
bool isThePedDead ( ped thePed )
```

### Required Arguments

-   **thePed :** The [ped](/docs/ped.md "wikilink") you want to check .

### Returns

Returns **true** if the [ped](/docs/ped.md "wikilink") is dead, **false** if a bad [ped](/docs/ped.md "wikilink") pointer was inserted or the [ped](/docs/ped.md "wikilink") is not dead .

### Example

<section name="Server / Client" class="both" show="true">
This example allows a player to use the command 'amidead' to see if they are dead or not.

``` lua
--Check if player is alive or dead and let them know in the chat box
function deathCheck ( thePlayer, commandName )
    if ( isThePedDead ( thePlayer ) ) then
         outputChatBox ( "You're dead... prepare to become a zombie.", thePlayer )
    else
         outputChatBox ( "Count your lucky stars, you're alive.", thePlayer )
    end
end
addCommandHandler ( "amidead", deathCheck )
```

</section>
**Made By:** Pαίй

See Also
--------
