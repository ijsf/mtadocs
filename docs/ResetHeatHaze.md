This function restores the default heat haze.

Syntax
------

``` lua
bool resetHeatHaze()
```

### Returns

Returns *true* if the heat haze was reset correctly, *false* otherwise.

Example
-------

This example resets the heat haze.

``` lua
addCommandHandler("reset2000",
  function()
    resetHeatHaze()
  end
)
```

[pl:resetHeatHaze](/pl:resetHeatHaze.md "wikilink")

See Also
--------
