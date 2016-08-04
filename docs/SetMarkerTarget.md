This function sets the 'target' for a marker. Only the *checkpoint* and *ring* marker types can have a target.

For *checkpoint* markers, the target is shown as an arrow aiming at the point specified.

For *ring* markers, the target is shown by rotating the whole ring so that it faces the point specified.

This function is most useful for setting up markers for races, where each marker points to the next one's position. (This is mostly used in races!)

Syntax
------

``` lua
bool setMarkerTarget ( marker theMarker, float x, float y, float z )    
```

### Required Arguments

-   **theMarker:** The marker to set the target of
-   **x:** The x axis of the coordinate to target the marker at
-   **y:** The y axis of the coordinate to target the marker at
-   **z:** The z axis of the coordinate to target the marker at

### Returns

Returns *true* if target was set, *false* otherwise.

Example
-------

Creates a marker in the center of the map and points it north.

``` lua
local marker = createMarker(0,0,0,"ring",7,255,0,0,255) --Creates a marker
setMarkerTarget(marker,3000,0,0) --Face the marker north
```

See Also
--------
