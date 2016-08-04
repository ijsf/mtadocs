In San Andreas, the water in the game world (rivers, lakes, seas) is defined through a large number of water polygons, which can be quadrilateral or triangular. A water element represents one such polygon. You can create water elements with [createWater](/docs/createwater.md "wikilink") or through a &lt;water/&gt; map element.

XML syntax
----------

``` xml
 />
```

### Required Attributes

-   **posX1, posY1, posZ1:** the position of the lower left (south-west) corner of the water surface.
-   **posX2, posY2, posZ2:** the position of the lower right (south-east) corner of the water surface.
-   **posX3, posY3, posZ3:** the position of the upper left (north-west) corner of the water surface.

### Optional Attributes

-   **posX4, posY4, posZ4:** the position of the upper right (north-east) corner of the water surface.

If only the first three corners are specified, a water triangle is created. If the fourth corner is also specified, a rectangle is created.

Related scripting functions
---------------------------

### Server

### Client

[Category:Element Types](/docs/category-element_types.md "wikilink")
