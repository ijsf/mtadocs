This function can be used to list out all the users a specified channel.

Syntax
------

``` lua
table ircGetChannelUsers ( ircbot theBot, string channel )
```

### Required Arguments

-   **theBot:** The ircbot which is connected to the channel
-   **channel:** The channel which users you want to get

### Returns

Returns a [table](/docs/table.md "wikilink") over all channel users. Returns an empty table if there's no users on that channel or *false* if invalid arguments were passed.

Example
-------

This example adds a command *listusers* which can be used to print out all users in the specified channel to the console.

``` lua
function printOutUsers ( thePlayer, commandName, name, channel )
    local theBot = ircGetBotByName ( name )
    if not theBot then
        outputConsole ( "There's no ircbot called " .. name .. "!", thePlayer )
    else
        if ircIsInChannel ( theBot, channel ) then
           local users = ircGetChannelUsers ( theBot, channel )
           if #users == 0 then
               outputConsole ( "There's no users on " .. channel .. "!", thePlayer )
           else
               outputConsole ( "There is " .. #users .. " on " .. channel .. ":", thePlayer ) 
               for key, value in ipairs ( users ) do
                   outputConsole ( "- " .. value, thePlayer )
               end
           end
        else
            outputConsole ( name .. " is not on " .. channel .. "!", thePlayer )
        end
    end
end
addCommandHandler ( "listusers", printOutUsers )
```

See Also
--------
