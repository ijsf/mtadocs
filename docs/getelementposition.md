The getElementPosition function allows you to retrieve the position coordinates of an element. This can be any real world element, including:

-   [Players](/docs/element/player.md "wikilink")
-   [Vehicles](/docs/element/vehicle.md "wikilink")
-   [Objects](/docs/element/object.md "wikilink")
-   [Pickups](/docs/element/pickup.md "wikilink")
-   [Markers](/docs/element/marker.md "wikilink")
-   [Collision shapes](/docs/element/collision_shape.md "wikilink")
-   [Blips](/docs/element/blip.md "wikilink")
-   [Radar areas](/docs/element/radar_area.md "wikilink")

Syntax
------

``` lua
float, float, float getElementPosition ( element theElement )
```

### Required Arguments

-   **theElement:** The element which you'd like to retrieve the location of

### Returns

Returns three *float*s indicating the position of the element, *x*, *y* and *z* respectively.

Example
-------

This example attaches a samsite on the player's vehicle.

``` lua
-- create the elegy;
myElegy = createVehicle ( 562, 1591.596680, -2495.323242, 18.098244 ) 
-- get the vehicle's position;
local x,y,z = getElementPosition( myElegy )
-- create the samsite;
samsite = createObject ( 3267, x, y, z + 3 )
-- attach the samsite to the elegy;
attachElementToElement ( samsite, myElegy, 0, 0, 0 )
```

See Also
--------

[de:GetElementPosition](/docs/de:getelementposition.md "wikilink")
