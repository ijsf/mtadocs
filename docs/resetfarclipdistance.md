This function resets the far clip distance to its default state.

Syntax
------

``` lua
bool resetFarClipDistance ( )
```

### Returns

Returns *true* if operation was successful, *false* otherwise.

Example
-------

This example will demonstrate basic functionality of the function.

``` lua
setFarClipDistance( 1200 )
outputDebugString( "Render distance: " .. getFarClipDistance( ) )
resetFarClipDistance( )
outputDebugString( "New render distance: " .. tostring( getFarClipDistance( ) ) )
```

See Also
--------
