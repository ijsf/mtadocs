The collision shape class represents invisible collision detection shapes that can be created in the GTA world. Collision shapes are typically used to detect physical entities moving through them and perform actions when they do.

The element type for this class is **colshape**.

XML syntax
----------

``` xml
<colcube posX="1024.768" posY="1248.1024" posZ="800.600" width="100" height="100" depth="100"/>
<colsphere posX="1024.768" posY="1248.1024" posZ="800.600" radius="100"/>
<coltube posX="1024.768" posY="1248.1024" posZ="800.600" radius="30" height="15"/>
<colrectangle posX="1024.768" posY="1248.1024" posZ="800.600" width="100" depth="61.8"/>
<colcircle posX="1024.768" posY="1248.1024" posZ="800.600" radius="30"/>
```

### Required Attributes

-   **posX**: A float representing the X position of the colshape.
-   **posY**: A float representing the Y position of the colshape.
-   **posZ**: A float representing the Z position of the colshape.
-   **radius**: The radius of the colshape (spheres, tubes and circles only).
-   **width**: The width of the colshape (rectangles and cubes only).
-   **depth**: The depth of the colshape (rectangles and cubes only).
-   **height**: The height of the colshape (cubes only).

### Optional Attributes

-   **dimension**: The dimension the colshape is in

Related scripting functions
---------------------------

[Category:Element Types](/Category:Element_Types.md "wikilink")

[it:Elemento/Collision shape](/it:Elemento/Collision_shape.md "wikilink")
