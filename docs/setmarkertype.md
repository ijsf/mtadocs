This function changes a marker's type. The type controls how the marker is displayed in the game. It's important that you use marker types that users are used to from the single player game. For example, checkpoints are used in races, rings are used for aircraft races, arrows are used for entering buildings etc.

Syntax
------

``` lua
bool setMarkerType ( marker theMarker, string markerType )
```

### Required Arguments

-   **theMarker**: A [marker](/docs/marker.md "wikilink") element referencing the specified marker.
-   **markerType**: A string denoting the marker type. Valid values are:

Returns
-------

Returns *true* if the marker type was changed, *false* if it wasn't or marker values were invalid.

Example
-------

This function changes all existing markers' type to the specified one.

``` lua
function changeAllMarkersType ( newMarkerType )
    -- we store a table with all markers
    local allMarkers = getElementsByType( "marker" )
    -- for each marker in it,
    for index, aMarker in ipairs(allMarkers) do
        -- set its type to the one passed to this function
        setMarkerType( aMarker, newMarkerType )
    end
end
```

See Also
--------
