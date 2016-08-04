Description
-----------

This function allows changing the icon of a checkpoint marker.

Syntax
------

``` lua
bool setMarkerIcon ( marker theMarker, string icon )
```

### Required Arguments

-   **theMarker:** The [marker](/docs/marker.md "wikilink") to change the visual style of
-   **icon:** A string referring to the type of icon, acceptable values are:
    -   **“none”**: No icon
    -   **“arrow”**: Arrow icon
    -   **“finish”**: Finish icon (at end of race)

Example
-------

This example creates a finish marker as you'd expect for the end of a race.

``` lua
theMarker = createMarker ( 1000, 1000, 1000, 0, 255, 0, 0 ) 
setMarkerIcon ( theMarker, "finish" )
```

See Also
--------
