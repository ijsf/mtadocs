This function returns the first pointer of the bot with the specified name. It's useful if you don't have access to the variable where bot was originally stored in .

Syntax
------

``` lua
ircbot ircGetBotByName ( string botName )
```

### Required Arguments

-   **botName:** The name of the ircbot you want to get.

### Returns

Returns the pointer if ircbot with specified name was found, *false* otherwise.

Example
-------

This example adds a command *getbotstate* which can be used to check the current state of an ircbot.

``` lua
function getIrcBotState ( thePlayer, commandName, botName )
    local theBot = ircGetBotByName ( botName )
    if theBot then
        outputChatBox ( botName .. " is currently " .. ircGetBotState ( theBot ) .. "." )
    else
        outputChatBox ( "There's no ircbot called " .. botName .. "!" )
    end
end
addCommandHandler ( "getbotstate", getIrcBotState )
```

See Also
--------
