This function sets the size of the specified marker.

Setting negative value will “flip” the marker, do nothing or make it invisible:

-   **cylinder** or **arrow**: upside down
-   **ring**: inside out
-   **checkpoint**: disappear
-   **corona**: bigger

Syntax
------

``` lua
bool setMarkerSize ( marker theMarker, float size )
```

### Required Arguments

-   **theMarker:** The [marker](/marker.md "wikilink") that you wish to set the size of.
-   **size:** A float representing new size of the marker.

### Returns

Returns *true* if successful, *false* if failed.

Example
-------

This example creates a cylinder marker at the position 1000, 1000, 1000 and sets its size to *2.5*.

``` lua
newmarker = createMarker ( 1000, 1000, 1000, "cylinder" )
setMarkerSize ( newmarker, 2.5 )
```

See Also
--------

### Client

### Server
