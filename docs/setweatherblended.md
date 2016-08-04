This function will change the current [weather](/docs/weather.md "wikilink") to another in a smooth manner, over the period of 2 in-game hours (unlike [setWeather](/setWeather.md "wikilink"), which sets a new weather instantly). To ensure this transition performs as expected, you should not call this function until [getWeather](/getWeather.md "wikilink") indicates that no transition is already being done.

Syntax
------

``` lua
bool setWeatherBlended ( int weatherID )
```

### Required Arguments

-   **weatherID:** The ID of the [weather](/docs/weather.md "wikilink") state you wish to set. Valid values are 0 to 255 inclusive.

### Returns

Returns *true* if successful, *false* if an invalid *weatherID* is passed.

Example
-------

This example sets the weather to sunny, then makes it change to a foggy over the period of two minutes (assuming that a in-game minute is a second in real time).

``` lua
-- Set the weather to sunny
setWeather ( 0 )
-- Blend the weather to foggy
setWeatherBlended ( 9 )
```

See Also
--------

[ru:setWeatherBlended](/docs/ru:setweatherblended.md "wikilink")
