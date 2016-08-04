XML syntax
----------

``` xml
<light posX="" posY="" posZ="" type="" radius="" color="" dirX="" dirY="" dirZ="" shadows="" />
```

### Required Attributes

-   **lightType:** An integer representing the type of light to create.

-   **posX:** A floating point number representing the X coordinate on the map.
-   **posY:** A floating point number representing the Y coordinate on the map.
-   **posZ:** A floating point number representing the Z coordinate on the map.

### Optional Arguments

-   **radius:** A floating point number representing the radius of the light.
-   **color:** The color of the light in HTML style format \#RRGGBB, defaults to black (invisible) if not specified.
-   **dirX:** A floating point number representing the light direction's X coordinate on the map.
-   **dirY:** A floating point number representing the light direction's Y coordinate on the map.
-   **dirZ:** A floating point number representing the light direction's Z coordinate on the map.
-   **shadows:** A boolean representing whether or not does the light cast shadows.

Related scripting functions
---------------------------

[Category:Element Types](/docs/category:element_types.md "wikilink")
