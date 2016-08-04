This function sets the current [weather](/weather.md "wikilink") to the given valid value. To change the weather gradually, see [setWeatherBlended](/setWeatherBlended.md "wikilink").

Syntax
------

``` lua
bool setWeather ( int weatherID )
```

### Required Arguments

-   **weatherID**: The ID of new [weather](/weather.md "wikilink"). Valid values are 0 to 255 inclusive.

### Returns

Returns *true* if the weather was set succesfully, *false* if an invalid *weatherID* was specified.

Example
-------

This example will change the weather to foggy.

``` lua
setWeather ( 9 )
outputChatBox ( "Weather changed to foggy!" )
```

See Also
--------

[ru:setWeather](/ru:setWeather.md "wikilink")
