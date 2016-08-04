Syntax
------

``` lua
bool setCameraShakeLevel ( int shakeLevel )
```

### Required arguments

-   **shakeLevel**: an integer between 0 and 255, which represents the camera shake intensity level.

### Returns

Returns *true* if the camera shake level was changed, *false* if the required argument is incorrect or missing.

Example
-------

This example adds a */camshake* command which allows any player to manually change its camera shake level.

``` lua
addCommandHandler( "camshake",
    function( _, level )
        local level = math.floor( level )
        if level and level >=0 and level <= 255 then
            setCameraShakeLevel( level )
            outputChatBox( "Camera shake level updated to " .. level .. "." )
        else
            outputChatBox( "Camera shake level must be between 0 and 255." )
        end
    end
)
```

See also
--------
