This function will tell you what is the current render distance.

Syntax
------

``` lua
float getFarClipDistance ( )
```

### Returns

Returns a *float* with the current render distance, *false* if the operation could not be completed.

Example
-------

This example will demonstrate basic functionality of the function.

``` lua
setFarClipDistance( 1200 )
outputDebugString( "Render distance: " .. getFarClipDistance( ) )
```

See Also
--------
