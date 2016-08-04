This function retrieves the server's port.

Syntax
------

``` lua
int getServerPort ( )
```

### Returns

An integer corresponding to the server's port.

Example
-------

This example Sends out the serverPort when you type: /serverport

``` lua
function outputServerPort ( )
        local serverPort = getServerPort() 
    outputChatBox (" Server Port: "..serverPort.." ") --Output Serverport in Chatbox
end
addCommandHandler ( "serverport", outputServerPort )  --add the command Handler
```

See Also
--------
