This function will return the responsible admin (nickname of the admin) of the specified [ban](/docs/ban.md "wikilink").

Syntax
------

``` lua
string getBanAdmin ( ban theBan )
```

### Required Arguments

-   **theBan:** The [ban](/docs/ban.md "wikilink") you want to return the admin of.

### Returns

Returns a *string* of the admin if everything was successful, *false* if invalid arguments are specified if there was no admin specified for the [ban](/docs/ban.md "wikilink").

Example
-------

``` lua
function outputBan(ban)
    local banned = getBanNick(ban) -- Get the name of the player who was banned
    local banner = getBanAdmin(ban) -- Get the name of the admin who banned the player
    local reason = getBanReason(ban) -- Get the reason the player was banned
    outputChatBox("-----BAN-----",getRootElement(),255,0,0)
    if (banned) then
        outputChatBox("Player banned: "..banned,getRootElement(),255,0,0) -- Output the player name who was banned
    end
    if (banner) then
        outputChatBox("Banner: "..banner,getRootElement(),255,0,0) -- Output the admin name who performed the ban
    end
    if (reason) then
        outputChatBox("Reason: "..reason,getRootElement(),255,0,0) -- outputt the reason the player was banned
    end
end
addEventHandler("onBan",getRootElement(),outputBan) -- When a player is banned trigger the outputBan function
```

See Also
--------

[ru:getBanAdmin](/docs/ru-getbanadmin.md "wikilink")
