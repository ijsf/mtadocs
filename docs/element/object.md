The object class represents static, 3-D models in the GTA world. Objects can only represent models created by the server, they cannot represent models that are part of the GTA's default landscape. Examples of objects include building models, roads, and terrain.

The element type of this class is **“object”**.

XML syntax
----------

``` xml
<object model="" posX="" posY="" posZ="" rotX="" rotY="" rotZ="" interior="" dimension="" scale="" collisions="" alpha="" frozen="" />
```

### Required Attributes

-   **model**: The ID of the object being created. Since GTA has thousands of objects, these are hard to document on the wiki. Instead, they can be found using the object browser in the map editor.
-   **posX**: A float representing the X position of the object.
-   **posY**: A float representing the Y position of the object.
-   **posZ**: A float representing the Z position of the object.

### Optional Attributes

-   **rotX**: A float representing the X rotation of the object in degrees.
-   **rotY**: A float representing the Y rotation of the object in degrees.
-   **rotZ**: A float representing the Z rotation of the object in degrees.
-   **interior**: The interior world the object is in.
-   **dimension**: The object's dimension number.

Related scripting functions
---------------------------

[Category:Element Types](/docs/category:element_types.md "wikilink") [ru:Element/Object](/docs/ru:element/object.md "wikilink") [it:Elemento/Oggetto](/docs/it:elemento/oggetto.md "wikilink")
