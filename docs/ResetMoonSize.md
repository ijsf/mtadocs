Syntax
------

``` lua
bool resetMoonSize ( )
```

### Returns

Returns true if the size of the moon was reset, false otherwise.

Example
-------

This example lets any player reset the size of the moon like /resetmoonsize

``` lua
function commandResetMoonSize(player, command)
    resetMoonSize()
end
addCommandHandler("resetmoonsize", commandResetMoonSize)
```

Requirements
------------

See Also
--------
