Gets the date and time at which a resource was last loaded in the server.

Syntax
------

### Required Arguments

-   **res:** the resource you want to know the load time of.

### Returns

Example
-------

This code outputs the date and time at which the scoreboard resource was last loaded.

``` lua
local res = getResourceFromName ( "scoreboard" )
if res then
    outputConsole ( "scoreboard was last loaded on: " .. getResourceLoadTime(res) )
end
```

See Also
--------
