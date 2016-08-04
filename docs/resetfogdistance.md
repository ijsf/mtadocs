This function resets the fog render distance to its default state.

Syntax
------

``` lua
bool resetFogDistance ( )
```

### Returns

Returns *true* if operation was successful, *false* otherwise.

Example
-------

This example will demonstrate basic functionality of the function.

``` lua
setFogDistance( 500 )
outputDebugString( "Fog render distance: " .. getFogDistance( ) )
resetFogDistance( )
outputDebugString( "New fog render distance: " .. tostring( getFogDistance( ) ) )
```

See Also
--------
