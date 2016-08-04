This function returns a [float](/float.md "wikilink") containing the size of the specified marker.

Syntax
------

``` lua
float getMarkerSize ( marker myMarker )
```

### Required Arguments

-   **myMarker**: The [marker](/marker.md "wikilink") that you wish to retrieve the size of.

### Returns

Returns a [float](/float.md "wikilink") containing the size of the specified marker.

Example
-------

This example creates a marker and outputs the size to everyone.

``` lua
-- Create a maker
newMarker = createMarker ( 1, 1000, 1000, 1000, 1,0,0 )
-- If the marker was created successfully then...
if ( newMarker ~= false ) then
    -- Tell everyone about it
    outputChatBox ( "Current marker size: " .. getMarkerSize ( newMarker ) )
end
```

See Also
--------
