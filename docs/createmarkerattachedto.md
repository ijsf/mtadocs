<lowercasetitle/>

This function creates a [marker](/docs/marker.md "wikilink") that is attached to an [element](/docs/element.md "wikilink"). This marker is a 3D model and will 'follow' the element that it is attached to around.

Syntax
------

``` lua
 )
```

### Required Arguments

-   **elementToAttachTo:** The [element](/docs/element.md "wikilink") to attach the marker to.

### Optional arguments

-   **theType**: The visual type of the marker to be created. Possible values:

-   **size**: The diameter of the marker to be created, in meters.
-   **r**: An integer number representing the amount of red to use in the colouring of the marker (0 - 255).
-   **g**: An integer number representing the amount of green to use in the colouring of the marker (0 - 255).
-   **b**: An integer number representing the amount of blue to use in the colouring of the marker (0 - 255).
-   **a**: An integer number representing the amount of alpha to use in the colouring of the marker (0 - 255 where 0 is transparent and 255 is opaque).
-   **visibleTo**: This defines which elements can see the marker. Defaults to visible to everyone. See [visibility](/docs/visibility.md "wikilink").
-   **xPosOffset:** The x offset, if you want the elements to be a certain distance from one another (default 0).
-   **yPosOffset:** The y offset (default 0).
-   **zPosOffset:** The z offset (default 0).

Code
----

<section name="Serverside/Clientside Script" class="both" show="true">
``` lua
function createMarkerAttachedTo(element, mType, size, r, g, b, a, visibleTo, xOffset, yOffset, zOffset)
    mType, size, r, g, b, a, visibleTo, xOffset, yOffset, zOffset = mType or "checkpoint", size or 4, r or 0, g or 0, b or 255, a or 255, visibleTo or getRootElement(), xOffset or 0, yOffset or 0, zOffset or 0
    assert(isElement(element), "Bad argument @ 'createMarkerAttachedTo' [Expected element at argument 1, got " .. type(element) .. "]") assert(type(mType) == "string", "Bad argument @ 'createMarkerAttachedTo' [Expected string at argument 2, got " .. type(mType) .. "]") assert(type(size) == "number", "Bad argument @ 'createMarkerAttachedTo' [Expected number at argument 3, got " .. type(size) .. "]") assert(type(r) == "number", "Bad argument @ 'createMarkerAttachedTo' [Expected number at argument 4, got " .. type(r) .. "]") assert(type(g) == "number", "Bad argument @ 'createMarkerAttachedTo' [Expected number at argument 5, got " .. type(g) .. "]") assert(type(b) == "number", "Bad argument @ 'createMarkerAttachedTo' [Expected number at argument 6, got " .. type(b) .. "]") assert(type(a) == "number", "Bad argument @ 'createMarkerAttachedTo' [Expected number at argument 7, got " .. type(a) .. "]") assert(isElement(visibleTo), "Bad argument @ 'createMarkerAttachedTo' [Expected element at argument 8, got " .. type(visibleTo) .. "]") assert(type(xOffset) == "number", "Bad argument @ 'createMarkerAttachedTo' [Expected number at argument 9, got " .. type(xOffset) .. "]") assert(type(yOffset) == "number", "Bad argument @ 'createMarkerAttachedTo' [Expected number at argument 10, got " .. type(yOffset) .. "]") assert(type(zOffset) == "number", "Bad argument @ 'createMarkerAttachedTo' [Expected number at argument 11, got " .. type(zOffset) .. "]")
    local m = createMarker(0, 0, 0, mType, size, r, g, b, a, visibleTo)
    if m then if attachElements(m, element) then return m end end return false
end
```

</section>
Author: HorrorClown (PewX)

See Also
--------
