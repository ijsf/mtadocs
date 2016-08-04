This function will force the specified player to resend their mod info, triggering the [onPlayerModInfo](/onPlayerModInfo.md "wikilink") event again.

Syntax
------

``` lua
bool resendPlayerModInfo ( player thePlayer )
```

### Required Arguments

-   **thePlayer**: A [player](/player.md "wikilink") object referencing the specified player

### Returns

Returns *true* if the mod info will be resent, *false* otherwise.

Example
-------

This example shows how to resend each players mod info during [onResourceStart](/onResourceStart.md "wikilink")

``` lua
addEventHandler( "onResourceStart", resourceRoot,
    function()
        for _,player in ipairs( getElementsByType("player") ) do
            resendPlayerModInfo( player )
        end
    end
)
```

Requirements
------------

See Also
--------
