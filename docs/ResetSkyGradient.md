This function allows restoring of a changed sky gradient as a result of [setSkyGradient](/setSkyGradient.md "wikilink").

Syntax
------

``` lua
bool resetSkyGradient()
```

### Returns

Returns *true* if sky color was reset correctly, *false* otherwise.

Example
-------

This example reset the sky gradient.

``` lua
addCommandHandler("resetsky",
  function()
    resetSkyGradient()
  end
)
```

See Also
--------

[ru:ResetSkyGradient](/ru:ResetSkyGradient.md "wikilink")
