This function can be used to list out all the channels a specified has connected to.

Syntax
------

``` lua
table ircGetConnectedChannels ( ircbot theBot )
```

### Required Arguments

-   **theBot:** The ircbot which connected channels you want to get

### Returns

Returns a [table](/table.md "wikilink") over all connected channels. Returns an empty table if the ircbot isn't connected to any channel.

Example
-------

This example adds a command *listchannels* which can be used to print out all channels where the specified ircbot is connected to the console.

``` lua
function printOutChannels ( thePlayer, commandName, name )
    local theBot = ircGetBotByName ( name )
    if not theBot then
        outputConsole ( "There's no ircbot called " .. name .. "!", thePlayer )
    else
        local channels = ircGetConnectedChannels ( theBot )
        outputConsole ( name .. " is on " .. #channels .. " channels:", thePlayer ) 
        for key, value in ipairs ( channels ) do
            outputConsole ( "- " .. value, thePlayer )
        end
    end
end
addCommandHandler ( "listchannels", printOutChannels )
```

See Also
--------
