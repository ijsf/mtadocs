The getElementPosition function allows you to retrieve the position coordinates of an element. This can be any real world element, including:

-   [Players](/docs/Element/Player.md "wikilink")
-   [Vehicles](/docs/Element/Vehicle.md "wikilink")
-   [Objects](/docs/Element/Object.md "wikilink")
-   [Pickups](/docs/Element/Pickup.md "wikilink")
-   [Markers](/docs/Element/Marker.md "wikilink")
-   [Collision shapes](/docs/Element/Collision_shape.md "wikilink")
-   [Blips](/docs/Element/Blip.md "wikilink")
-   [Radar areas](/docs/Element/Radar_area.md "wikilink")

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

[de:GetElementPosition](/docs/de:GetElementPosition.md "wikilink")
