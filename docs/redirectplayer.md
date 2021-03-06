This function redirects the player to a specified server.

Syntax
------

``` lua
bool redirectPlayer ( player thePlayer, string serverIP, int serverPort, [ string serverPassword ] )
```

### Required Arguments

-   **thePlayer:** The player you want to redirect
-   **serverIP:** The IP address (or domain name that resolves to the IP address) of the server you want to redirect the player to. Use an empty string to reconnect to the same server.
-   **serverPort:** The game port of the server you want to redirect the player to, this is usually 22003. Set to zero to use the same port as the current server.

### Optional Arguments

-   **serverPassword:** The password for the server if it's protected

### Returns

Returns *true* if the player was redirected successfully, *false* if bad arguments were passed.

Example
-------

This example adds a “joinserver” command using the syntax, "/joinserver serverIP serverPort \[serverPassword\]".

``` lua
function joinserverHandlerFunction (playerSource, commandName, serverIP, serverPort, serverPassword)
    if serverIP and serverPort then --if IP and Port were specified
        if serverPassword then --if also a password was specified
            redirectPlayer (playerSource, serverIP, tonumber(serverPort), serverPassword) --redirect the player
        else -- else if no password was specified
            redirectPlayer (playerSource, serverIP, tonumber(serverPort))  --redirect the player without using the serverPassword parameter
        end
    else -- if no IP or Port have been specified
        outputChatBox ("Error! Correct Syntax: /joinserver IP Port [Password]", playerSource) --output an Error message to the chatbox
    end
end

addCommandHandler ("joinserver", joinserverHandlerFunction) 
```

See Also
--------
