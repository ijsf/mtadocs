The resource makes it possible to render water in interiors, where normaly wouldn't be visible. It draws a line material and applies a shader effect that mimicks the gta water effect.

Overview
--------

This resource provides few convenient exported functions. Here you can download an example of how to use that: [Download!](http://www.solidfiles.com/d/73d0427849/)

Exported functions
------------------

#### createWaterInInterior

<section name="Client" class="client" show="true">
This function creates water.

``` lua
 )
```

### Required Arguments

-   **x1, y1, z1:** position of bottom left (south-west) corner.
-   **x2, y2, z2:** position of bottom right (south-east) corner.
-   **x3, y3, z3:** position of top left (north-west) corner.
-   **x4, y4, z4:** position of top right (north-east) corner.
-   **intID:** interior in which the water is to be created.

### Optional Arguments

-   **effectType:** effect type (0 - classic water, 1- watershine)

### Returns

Returns water element if successful, *false* otherwise.

</section>
#### createWaterInInteriorRadius

<section name="Client" class="client" show="true">
This function creates water (using different data).

``` lua
 )
```

### Required Arguments

-   **x, y, z:** position of the top-central point.
-   **radius:** define the radious of water box to be created.
-   **intID:** interior in which the water is to be created.

### Optional Arguments

-   **effectType:** effect type (0 - classic water, 1- watershine)

### Returns

Returns water element if successful, *false* otherwise.

</section>
#### destroyWaterInInterior

<section name="Client" class="client" show="true">
This function destroys previously created water.

``` lua
bool exports.interior_flood:destroyWaterInInterior( element )
```

### Required Arguments

-   **element:** Previously created waterInInterior element.

### Returns

Returns 'true' if successful, *false* otherwise.

</section>
#### attachMaterialToWaterInInterior

<section name="Client" class="client" show="true">
This function attaches water surface material to existing water in interior.

``` lua
 )
```

### Required Arguments

-   **x, y, z:** position of the top-central point. The 'z' position will be corrected by height of the existing water.
-   **radius:** define the radious of the effect.
-   **intID:** interior in which the water is to be created.

### Optional Arguments

-   **effectType:** effect type (0 - classic water, 1- watershine)

### Returns

Returns water element if successful, *false* otherwise.

</section>
#### detachMaterialFromWaterInInterior

<section name="Client" class="client" show="true">
This function destroys the surface material created with attachMaterialToWaterInInterior.

``` lua
bool exports.interior_flood:detachMaterialFromWaterInInterior( element )
```

### Required Arguments

-   **element:** Previously created waterSurface element.

### Returns

Returns 'true' if successful, *false* otherwise.

</section>
Examples
--------

``` lua
exports.interior_flood:createWaterInInteriorRadius(-28.628,-83.787,1003.5,15,18,1)
```

This creates visible water in interior 18.

``` lua
exports.interior_flood:createWaterInInterior(-290,-290,40,290,-290,40, -290, 290, 40, 290, 290, 40,0,1 )
```

This creates visible water in interior 0.

``` lua
local someWater = exports.interior_flood:createWaterInInterior(-290,-290,40,290,-290,40, -290, 290, 40, 290, 290, 40,0,1 )
exports.interior_flood:destroyWaterInInterior(someWater)
```

This creates and destroys visible water in interior 0.

Of course when you want to use theese functions in your resources you have to include the interior\_flood resource in meta.

See Also
--------

[Resource Download](https://community.multitheftauto.com/index.php?p=resources&s=details&id=8234)
