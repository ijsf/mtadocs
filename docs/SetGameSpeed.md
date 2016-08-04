This function sets the game speed to the given value.

Syntax
------

``` lua
bool setGameSpeed ( float value )
```

### Required Arguments

-   **value**: The float value of the game speed (Range 0 - 10)

### Returns

Returns *true* if the gamespeed was set successfully, *false* otherwise. The normal game speed is '1'.

Example
-------

<section name="Server" class="server" show="true">
``` lua
addCommandHandler("setgamespeed",
  function(sourcePlayer, command, value)
    setGameSpeed(tonumber(value))
  end
)
```

</section>
<section name="Client" class="client" show="true">
``` lua
addCommandHandler("setgamespeed",
  function(command, value)
    setGameSpeed(tonumber(value))
  end
)
```

</section>
See Also
--------

[ru:setGameSpeed](/docs/ru:setGameSpeed.md "wikilink")
