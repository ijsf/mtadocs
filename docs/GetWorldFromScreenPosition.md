This function allows you to retrieve the world position corresponding to a 2D position on the screen, at a certain depth.

If you want to detect what element is at a particular point on the screen, use [processLineOfSight](/docs/processLineOfSight.md "wikilink") between the camera position and the position returned from this function when passed a high depth value (100 or so, depending how far away you want to detect elements at).

As expected, setting 0 as the distance will cause the point retrived to be within the camera itself. That means thaf drawing any 3D thing in that point would result in it not being visible. Depending on the camera near clip distance, however, the minimum distance to be able to view it can vary.

Syntax
------

``` lua
float, float, float getWorldFromScreenPosition ( float x, float y, float depth )
```

### Required Arguments

-   **x:** A float value indicating the x position on the screen, in pixels.
-   **y:** A float value indicating the y position on the screen, in pixels.
-   **depth:** A float value indicating the distance from the camera of the point whose coordinates we are retrieving, in units.

### Returns

Returns three *x*, *y*, *z* [floats](/docs/float.md "wikilink") indicating the world position if successful, *false* otherwise.

Example
-------

This example binds the local player's "**i**" key to a function that creates an explosion in the middle of the screen.

``` lua
function explosion ()
  local w, h = guiGetScreenSize ()
  local x, y, z = getWorldFromScreenPosition ( w/2, h/2, 10 )
  createExplosion ( x, y, z, 11 )
end
bindKey ( "i", "down", explosion )
```

See Also
--------
