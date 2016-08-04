This function changes the heat haze effect.

Syntax
------

``` lua
bool setHeatHaze ( int intensity, [ int randomShift = 0, int speedMin = 12, int speedMax = 18, int scanSizeX = 75, int scanSizeY = 80, int renderSizeX = 80, int renderSizeY = 85, bool bShowInside = false ] )
```

### Optional Arguments

### Returns

Returns *true* if the heat haze effect was set correctly, *false* if invalid values were passed.

Example
-------

**Example 1:** This example turns the heat haze effect off:

``` lua
setHeatHaze ( 0 )
```

**Example 2:** This example will have an interesting effect:

``` lua
setHeatHaze ( 50, 20, 0, 500, 200, 100, 50, 20, true )
```

See Also
--------
