This function will return the unbanning time of the specified [ban](/docs/ban.md "wikilink") in **seconds**.

Syntax
------

``` lua
int getUnbanTime ( ban theBan )
```

### Required Arguments

-   **theBan:** The [ban](/docs/ban.md "wikilink") in which you wish to retrieve the unban time of.

### Returns

-   Returns an integer of the unbanning time in the format of seconds from the year 1970. Use in conjunction with [getRealTime](/docs/getrealtime.md "wikilink") in order to retrieve detailed information.
-   Returns **false** if invalid arguments are specified or if there was no unbanning time specified for the [ban](/docs/ban.md "wikilink").

Example
-------

``` lua
function listBans ()
    local bansList = getBans() -- Return a table of all the bans.
 
    for banID, ban in ipairs ( banList ) do -- For every ban do the following...
        local nick = getBanNick ( ban ) -- Get the IP of the ban
                local timetounban = getUnbanTime ( ban ) -- get the time to wait of the banned player
        if nick then
            outputChatBox ( "Ban #" .. banID .. ": " .. nick.." || Time to unban: "..timetounban , source, 255, 0, 0 ) -- Output the baninfo
        end
    end
end
addCommandHandler ( "bans", listBans ) -- Add "/bans" as the trigger for the function.
```

See Also
--------

[ru:getUnbanTime](/docs/ru:getunbantime.md "wikilink")
