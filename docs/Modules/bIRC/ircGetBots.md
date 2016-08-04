This function can be used to list out all created s.

Syntax
------

``` lua
table ircGetBots ()
```

### Required Arguments

*None*

### Returns

Returns a [table](/docs/table.md "wikilink") over all created ircbots. Returns an empty table if no ircbots exist.

Example
-------

This example adds a command *listbots* which can be used to print out all currently available ircbots along with their names to console.

``` lua
function printOutIrcBots ( thePlayer )
    local ircBots = ircGetBots ()
    if #ircBots == 0 then
        outputConsole ( "There are no ircbots!", thePlayer )
    else
        outputConsole ( "There's " .. #ircBots .. " ircbots:", thePlayer ) 
        for key, value in ipairs ( ircBots ) do
            outputConsole ( "- " .. ircGetName ( value ), thePlayer )
        end
    end
end
addCommandHandler ( "listbots", printOutIrcBots )
```

See Also
--------
