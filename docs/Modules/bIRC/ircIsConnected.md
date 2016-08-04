This function is used to check whether the specified is connected to a server.

Syntax
------

``` lua
bool ircIsConnected ( ircbot theBot )
```

### Required Arguments

-   **theBot:** The ircbot which connection state you want to check.

### Returns

Returns *true* if the ircbot is connected, *false* otherwise.

Example
-------

This example adds a command *isbotconnected* which can be used to determine if a certain bot is connected or not.

``` lua
function checkIsBotConnected ( thePlayer, commandName, botName )
    local theBot = ircGetBotByName ( botName )
    if theBot then
        if ircIsConnected ( theBot )
            outputChatBox ( "Yes, " .. botName .. " is connected!", thePlayer )
        else
            outputChatBox ( "Nope, " .. botName .. " isn't connected!", thePlayer )
        end
    else
        outputChatBox ( "There is no bot called " .. botName .. "!", thePlayer )
    end
end
addCommandHandler ( "isbotconnected", checkIsBotConnected )
```

See Also
--------
