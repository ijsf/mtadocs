This function is used to set the size of the sun.

Syntax
------

``` lua
bool setSunSize ( int Size )
```

### Required Arguments

-   **Size:** The size you want the sun to be in the sky.

### Returns

Returns true if the size of the sun was set, false otherwise.

Example
-------

This example lets any player set the size of the sun like /setsunsize 2

``` lua
function commandSetSunSize(player, command, size)
    local size = tonumber(size)
    if (not size) then return end -- They didn't use a number
    setSunSize(size)
end
addCommandHandler("setsunsize", commandSetSunSize)
```

See Also
--------
