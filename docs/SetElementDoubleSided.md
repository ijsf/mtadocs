This function allows you to set the double-sidedness of an element's model. When an element's model is double-sided, it's back facing triangles become visible.

Possible uses of double-sidedness are: Elimination of invisible walls, using buildings as enclosures, using inverted landmasses as large pits or to make cave networks. It can also remove the need to add extra triangles to custom models when trying to make them appear solid from all directions.

Syntax
------

``` lua
bool setElementDoubleSided ( element theElement, bool enable )
```

### Required Arguments

-   **theElement:** The element in which you'd like to set the double-sidedness of.
-   **enable :** Set to true/false to enable/disable double-sidedness.

### Returns

Returns *true* if **theElement** is valid, *false* otherwise.

Example
-------

<section name="Server" class="server" show="true">
This example shows how to set the double-sidedness of an object in a map file.

``` lua
<map mod="deathmatch">
    <object name="object (1)" posX="100" posY="200" posZ="20" rotX="0" rotY="0" rotZ="0" doublesided="true" model="3860"/>
</map>
```

</section>
See Also
--------
