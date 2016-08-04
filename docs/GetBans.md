This function will return a table containing all the [bans](/ban.md "wikilink") present in the server's banlist.xml.

Syntax
------

``` lua
table getBans ( )
```

### Returns

Returns a [table](/table.md "wikilink") containing all the [bans](/ban.md "wikilink").

Example
-------

<section name="Example 1: Server" class="server" show="true">
This example lists every ban when somebody types "/bans". WARNING: This will spam chat (for the player that executed the command) if the server has a lot of bans.

``` lua
function listBans ( playerSource )
local banList = getBans() -- Return a table of all the bans.
    --
    for banID, ban in ipairs ( banList ) do -- For every ban do the following...    
        --
        local nick = getBanNick ( ban ) -- Get the IP of the ban
        --
        if nick then
            outputChatBox ( "Ban #" .. banID .. ": " .. nick, playerSource , 255, 0, 0, true ) -- Output the ban.
        end
        --
    end
    --
end
addCommandHandler ( "bans", listBans ) -- Add "/bans" as the trigger for the function.
```

</section>
See Also
--------

[ru:getBans](/ru:getBans.md "wikilink")
