This function retrieves the server's http port.

Syntax
------

``` lua
int getServerHttpPort ( )
```

### Returns

An integer corresponding to the server's http port.

Example
-------

This example outputs server's HTTP port to the chat box when player uses command *getHttpPort*

``` lua
addCommandHandler("getHttpPort",
function(player, command)

outputChatBox("HTTP port of this server is: " .. getServerHttpPort(), player, 0, 255, 0)

end)
```

See Also
--------
