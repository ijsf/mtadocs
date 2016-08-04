This function changes the distance at which fog appears. Keep in mind that this function doesn't change the distance of render.

Syntax
------

``` lua
bool setFogDistance ( float distance )
```

### Arguments

-   **distance:** distance in GTA units at which fog will appear. Very short or negative distances will cause graphical bugs to the players.

### Returns

Returns *true* if the distance changed successfully, *false* if bad arguments were passed.

Example
-------

<section name="Server" class="server" show="true">
This example makes any weather very clear when the resource that contains it starts.

``` lua
function makeWeatherClear()
    setFogDistance(500) -- Set the fog distance to 500 units, so any weather will appear to be extremely clear
end
addEventHandler("onResourceStart", resourceRoot, makeWeatherClear)
```

</section>
See Also
--------
