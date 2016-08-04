This function is used to determine whether or not a ped is on the ground. This is for on-foot usage only.

Syntax
------

``` lua
bool isPedOnGround ( ped thePed )
```

### Required Arguments

-   **thePed:** The [ped](/ped.md "wikilink") you are checking.

### Returns

Returns *true* if the ped is on foot and on the ground, *false* otherwise, even if he is in a car that stands still or on object outside world map.

Example
-------

<section name="Server" class="server" show="true">
This example checks if the player who enters the 'amiflying' command is on the ground and outputs a message.

``` lua
function isHeFlying ( sourcePlayer )
    if isPedOnGround ( sourcePlayer ) then
        outputChatBox ( "No, you're not flying, you're just stoned!", sourcePlayer )
    else
        outputChatBox ( "Is it a bird, is it a plane... No it's " .. getPlayerName ( sourcePlayer ) .. "!", sourcePlayer )
    end
end
addCommandHandler ( "amiflying", isHeFlying )
```

</section>
Issues
------

See Also
--------
