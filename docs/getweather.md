This function returns the current [Weather](/docs/weather.md "wikilink") ID.

Syntax
------

``` lua
int, int getWeather()
```

### Returns

Returns two integers indicating the weather type that is currently active. The first integer says what weather is currently considered to be active. The second integer is the weather id that is being blended into if any, otherwise it is *nil*.

Example
-------

This example outputs the current weather ID in that chat box.

``` lua
local weatherID = getWeather()
outputChatBox ( "The current weather ID is " .. weatherID )
```

See Also
--------

[ru:getWeather](/docs/ru:getweather.md "wikilink")
