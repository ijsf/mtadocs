The marker class represents colored, 3D shapes in the GTA world. There are several types of markers, including cylinders and checkpoints. In scripts, markers are often used to mark spots and trigger some sort of action when a player goes into them.

The element type of this class is **“marker”**.

The size of the marker cannot be specified from XML and defaults to 4.0.

XML syntax
----------

``` xml
<marker posX="" posY="" posZ="" type="" .../>
```

### Required Attributes

-   **posX**: A float representing the X position of the marker.
-   **posY**: A float representing the Y position of the marker.
-   **posZ**: A float representing the Z position of the marker.

### Optional Attributes

-   **type:** The visual type of the marker to be created. Possible values:

-   **color:** The color of the marker in HTML style format \#RRGGBB, defaults to red if not specified.

Related scripting functions
---------------------------

[Category:Element Types](/Category:Element_Types.md "wikilink")

[it:Elemento/Marker](/it:Elemento/Marker.md "wikilink") [ru:Элемент/Маркер](/ru:Элемент/Маркер.md "wikilink")
