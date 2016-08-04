Creates an area of [water](/docs/water.md "wikilink").

The largest possible size of a water area is 5996×5996. Also be aware that the function will change all x and y coordinates you specify into even integer numbers if necessary: this is because of a limitation of San Andreas.

You are able to give the water a shallow water effect, which practically changes the water invisible to the eye. However, all elements still work the same way as without the shallow effect - allowing swimming, diving, vehicles to sink, etc.

Syntax
------

``` lua
 )
```

[thumb|Example of water quadrant.|284x230px](/docs/image-waterareas.jpg.md "wikilink")

### Required Arguments

-   **x1, y1, z1:** position of bottom left (south-west) corner.
-   **x2, y2, z2:** position of bottom right (south-east) corner.
-   **x3, y3, z3:** position of top left (north-west) corner.

*Note: Only 3 coords creates a triangle*

### Optional Arguments

-   **x4, y4, z4:** position of top right (north-east) corner.
-   **bShallow:** gives the water a shallow water effect.

### Returns

Returns a water element if successful, *false* otherwise. The water element can be repositioned with [setElementPosition](/docs/setelementposition.md "wikilink") and destroyed with [destroyElement](/docs/destroyelement.md "wikilink").

Example
-------

<section name="Client" class="client" show="true">
Example code for creating a water area to cover the entire San Andreas Map (flood the cities). Also, [setWaterLevel](/docs/setwaterlevel.md "wikilink") is used to raise the existing rivers and lakes.

``` lua
-- Setting water properties.
height = 40
SizeVal = 2998
-- Defining variables.
southWest_X = -SizeVal
southWest_Y = -SizeVal
southEast_X = SizeVal
southEast_Y = -SizeVal
northWest_X = -SizeVal
northWest_Y = SizeVal
northEast_X = SizeVal
northEast_Y = SizeVal

-- OnClientResourceStart function that creates the water.
function thaResourceStarting( )
    water = createWater ( southWest_X, southWest_Y, height, southEast_X, southEast_Y, height, northWest_X, northWest_Y, height, northEast_X, northEast_Y, height )
    setWaterLevel ( height )
end
addEventHandler("onClientResourceStart", resourceRoot, thaResourceStarting)
```

</section>
<section name="Client" class="client" show="true">
This example creates water at the given coordinates and sets the height of the water level to 20 for when the client joins.

``` lua
function thaResourceStarting( )
    water = createWater ( 1866, -1444, 10, 1968, -1442, 10, 1866, -1372, 10, 1968, -1370, 10 )
    setWaterLevel ( water, 20 )
end
addEventHandler("onClientResourceStart", getResourceRootElement(getThisResource()), thaResourceStarting)
```

</section>
Issues
------

See Also
--------
