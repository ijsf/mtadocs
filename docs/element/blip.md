The blip class represents small icons or blips that can be shown on a player's radar.

The element type of this class is **“blip”**. The list of blip icons are available on the [Blip Icons](/docs/blip_icons.md "wikilink") page.

XML syntax
----------

``` xml
<blip posX="" posY="" posZ="" icon="" color="" dimension="" ordering=""/>
```

### Required Attributes

-   **posX**: A float representing the X position of the vehicle.
-   **posY**: A float representing the Y position of the vehicle.
-   **posZ**: A float representing the Z position of the vehicle.

### Optional Attributes

-   **color:** The color of the icon in HTML-style format (i.e. \#RRGGBB). Defaults to blue if not specified.
-   **icon:** The icon of the blip. Defaults to 0 if not specified.
-   **dimension:** The dimension of the blip. Defaults to 0 if not specified.
-   **ordering:** The Z-level ordering of the blip. Defaults to 0 if not specified.

Related scripting functions
---------------------------

### Client

### Server

[Category:Element Types](/docs/category:element_types.md "wikilink") [it:Elemento/Blip](/docs/it:elemento/blip.md "wikilink")
