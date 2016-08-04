Syntax
------

``` lua
bool setBanReason( ban theBan, string theReason )
```

### Required Arguments

-   **theBan:** The [ban](/docs/ban.md "wikilink") that you wish to set the reason of.
-   **theReason:** the new reason (max 60 characters).

### Returns

Returns *true* if the new reason was set successfully, *false* otherwise.

Example
-------

This example adds the command *setreason* which can be used to change the reason of a ban by nickname of the banned player. *For example: setreason someguy reason.*

``` lua
function setReason (player,cmd,name,...)
    local reason = table.concat({...}," ")
    if name and reason then
        local bans = getBans()
        for i,v in ipairs(bans)do
            if getBanNick(v) == name then
                setBanReason(v,reason)
                outputChatBox("Successfully edited the new Ban Reason.",player,0,125,0)
            end
        end
    end
end
addCommandHandler("setreason", setReason)
```

See Also
--------

[ru:setBanReason](/docs/ru-setbanreason.md "wikilink")
