This function returns a [string](/docs/string.md "wikilink") containing the IP address of the [player](/player.md "wikilink").

Syntax
------

``` lua
string getPlayerIP ( player thePlayer )
```

### Required Arguments

-   **thePlayer:** The [player](/docs/player.md "wikilink") element you want to get the IP of.

### Returns

Returns a [string](/docs/string.md "wikilink") containing the requested players's IP, or *false* if the player passed to the function is invalid.

Example
-------

This example prints a player's IP to the chat.

``` lua
function printIp ( thePlayer )
    outputChatBox ( "IP: " .. getPlayerIP ( thePlayer ), thePlayer )
end
addCommandHandler ( "ip", printIp )
```

See Also
--------

[de:getPlayerIP](/docs/de:getPlayerIP.md "wikilink") [ru:getPlayerIP](/ru:getPlayerIP.md "wikilink")
