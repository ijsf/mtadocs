This function will remove a specific [ban](/docs/ban.md "wikilink").

Syntax
------

``` lua
bool removeBan ( ban theBan [, player responsibleElement = nil ] )
```

### Required Arguments

-   **theBan:** The [ban](/docs/ban.md "wikilink") to be removed.

### Optional Arguments

-   **responsibleElement:** The element that is responsible for removing the [ban](/docs/ban.md "wikilink") element. This can be a player or the root ([getRootElement](/docs/getrootelement.md "wikilink")()).

### Returns

Returns *true* if the [ban](/docs/ban.md "wikilink") was removed succesfully, *false* if invalid arguments are specified.

Example
-------

This example removes all the bans when the resource is started and outputs to everyone the players.

``` lua
addEventHandler("onResourceStart",resourceRoot,function()
    bans = getBans()
    for i,d in ipairs(bans)do
        nick = getBanNick(d)
        if(removeBan(d))then
            outputChatBox(nick.."has been removed from ban",root)
        end
    end
end)
```

This example removes the ban for IP 1.2.3.4

``` lua
for _,ban in ipairs(getBans())do
    if getBanIP(ban) == "1.2.3.4" then
        removeBan(ban)
    end
end
```

See Also
--------

[ru:removeBan](/docs/ru-removeban.md "wikilink")
