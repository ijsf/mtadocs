This function will tell you what is the current fog render distance.

Syntax
------

``` lua
float getFogDistance ( )
```

### Returns

Returns a *float* with the current fog render distance, *false* if the operation could not be completed.

Example
-------

This example will demonstrate basic functionality of the function.

``` lua
function fogDistance( )
    outputChatBox( "Fog distance is: " .. tostring( getFogDistance( ) ) )
end
addCommandHandler( "fog", fogDistance )
```

See Also
--------
