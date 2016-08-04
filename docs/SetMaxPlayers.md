This function sets the maximum number of player slots on the server.

**Note**: This function can not set more than <maxplayers> as defined in [mtaserver.conf](/mtaserver.conf.md "wikilink"). (To find out the <maxplayers> value, use getServerConfigSetting(“maxplayers”))

Syntax
------

``` lua
bool setMaxPlayers ( int slots )
```

### Required Arguments

-   **slots:** Maximum number of player slots on the server.

### Returns

Returns *true* if number of player slots was successfully changed, *false* or *nil* otherwise.

Example
-------

This example set server slots count to half value from current value.

``` lua
local curMaxPlayers = getMaxPlayers()
local newMaxPlayers = math.ceil( curMaxPlayers / 2 )

setMaxPlayers( newMaxPlayers )
```

This example resets the server slots count to the value from mtaserver.conf

``` lua
setMaxPlayers( tonumber( getServerConfigSetting("maxplayers") ) )
```

See Also
--------
