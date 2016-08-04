This function is used to determine whether or not a player is on the ground. This is for on-foot usage only.

Syntax
------

<section name="Server and client" class="both" show="true">
``` lua
bool isPlayerOnGround ( player thePlayer )
```

### Required Arguments

-   **thePlayer:** The [player](/docs/player.md "wikilink") you are checking.

### Returns

Returns *true* if the player is on foot and on the ground, *false* otherwise, even if he is in a vehicle capable of flying.

</section>
Example
-------

<section name="Serverside example" class="server" show="true">
This example checks if the player who enters the 'amiflying' command is on the ground and outputs a message.

     [lua]
    function isHeFlying ( sourcePlayer )
        if ( isPlayerOnGround ( sourcePlayer ) ) then
            outputChatBox ( "No, you're not flying, you're just stoned!", sourcePlayer )
        else
            outputChatBox ( "Is it a bird, is it a plane... No it's " .. getClientName ( sourcePlayer ) .. "!", sourcePlayer )
        end
    end
    addCommandHandler ( "amiflying", isHeFlying )

</section>
See Also
--------
