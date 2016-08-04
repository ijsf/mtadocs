This function returns a string containing the IP address of the client.

Syntax
------

``` lua
string getClientIP ( client theClient )
```

### Required Arguments

-   **theClient:** The client [element](/docs/element.md "wikilink") (player or admin) you want to get the IP of.

### Returns

Returns a string containing the requested client's IP, or *false* if the client passed to the function is invalid.

Example
-------

This example prints a player's IP to the chat.

``` lua
function printIP ( thePlayer, command )
    outputChatBox ( getClientName ( thePlayer ) .. "'s IP is: " .. getClientIP ( thePlayer ) )
end
addCommandHandler ( "ip", printIP )
```

See Also
--------
