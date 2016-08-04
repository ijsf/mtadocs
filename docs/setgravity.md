This function sets the server's gravity level.

**Note:** This does not effect peds/players; to set ped/player gravity use [setPedGravity](/docs/setpedgravity.md "wikilink").

**Note:** Setting the gravity level to different values on clients can cause animation bugs (players floating across ground because players see different fall animation.)

Syntax
------

``` lua
bool setGravity ( float level )
```

### Required Arguments

-   **level**: The level of gravity (default is **0.008**).

### Returns

Returns *true* if gravity was changed, *false* otherwise.

Example
-------

``` lua
function grav ( sourcePlayer, command, level )
    setGravity ( tonumber(level) )
end
addCommandHandler ( "setgravity", grav )
```

See Also
--------

[ru:setGravity](/docs/ru-setgravity.md "wikilink")
