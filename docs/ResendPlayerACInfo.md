Syntax
------

``` lua
bool resendPlayerACInfo ( player thePlayer )
```

### Required Arguments

-   **thePlayer**: A [player](/player.md "wikilink") object referencing the specified player

### Returns

Returns *true* if the AC info will be resent, *false* otherwise.

Example
-------

This example shows how to resend each players AC info during [onResourceStart](/onResourceStart.md "wikilink")

``` lua
addEventHandler( "onResourceStart", resourceRoot,
    function()
        for _,player in ipairs( getElementsByType("player") ) do
            resendPlayerACInfo( player )
        end
    end
)
```

Requirements
------------

See Also
--------