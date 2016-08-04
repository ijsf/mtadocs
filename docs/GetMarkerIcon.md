This function returns the icon name for a marker.

Syntax
------

``` lua
string getMarkerIcon ( marker theMarker )
```

### Required Arguments

-   **theMarker**: A [marker](/marker.md "wikilink") element referencing the specified marker.

### Returns

Returns *false* if the marker passed is invalid or a string containing one of the following:

-   **“none”**: No icon
-   **“arrow”**: Arrow icon
-   **“finish”**: Finish (end-race) icon

Example
-------

``` lua
newmarker = createMarker ( 1000, 1000,1000, "checkpoint", 255, 0, 0 )
icon = getMarkerIcon ( newmarker )
outputChatBox ( "The default marker icon is " .. icon )
```

See Also
--------
