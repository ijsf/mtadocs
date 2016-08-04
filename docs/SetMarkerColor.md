This function sets the color of the specified marker by modifying the values for red, green and blue.

Syntax
------

``` lua
bool setMarkerColor ( marker theMarker, int r, int g, int b, int a )
```

### Required Arguments

-   **theMarker:** The [marker](/docs/marker.md "wikilink") that you wish to set the color of.
-   **r:** The amount of red in the final color (0 to 255).
-   **g:** The amount of green in the final color (0 to 255).
-   **b:** The amount of blue in the final color (0 to 255).
-   **a:** The amount of alpha in the final color (0 to 255).

Example
-------

``` lua
newmarker = createMarker ( 1000, 1000, 1000, 1, 255, 0, 0, 255 )  -- Create a red marker
setMarkerColor ( newmarker, 0, 255, 0, 255 )                      -- Turn the red marker into a green one
```

See Also
--------
