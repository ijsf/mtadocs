Syntax
------

``` lua
bool setUnbanTime( ban theBan, int theTime )
```

### Required Arguments

-   **theBan:** The [ban](/docs/ban.md "wikilink") of which to change the unban time of
-   **theTime:** the new unban time

### Returns

Returns *true* if changed successfully, *false* otherwise.

Example
-------

``` lua
addCommandHandler("banMe",
function (player)
local ban = banPlayer(player)
setUnbanTime(ban, 500)
end
)
```

See Also
--------

[ru:setUnbanTime](/docs/ru:setUnbanTime.md "wikilink")
