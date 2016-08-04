Syntax
------

``` lua
bool setBanAdmin ( ban theBan, string theAdmin )
```

### Required Arguments

-   **theBan:** The [ban](/docs/ban.md "wikilink") you want to change the admin of.
-   **theAdmin:** The new admin.

### Returns

Returns *true* if changed, *false* otherwise.

Example
-------

This example changes the ban admin to the admin's IP (If it's a player), when someone gets banned.

``` lua
function banHappened(theBan)
    if getElementType(source) == "player" then
        local adminIP = getPlayerIP(source)
        setBanAdmin(theBan,adminIP)
    end
end

addEventHandler( "onBan", getRootElement(), banHappened )
```

See Also
--------

[ru:setBanAdmin](/docs/ru:setBanAdmin.md "wikilink")
