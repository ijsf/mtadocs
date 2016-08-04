<lowercasetitle></lowercasetitle>

This function can be used to get the elements within a markers collision area.

Syntax
------

``` lua
table getElementsWithinMarker ( marker theMarker )
```

### Required Arguments

-   **theMarker:** The marker element that you want to see what's inside.

### Returns

Returns a *table* containing each element that's inside the marker just like [getElementsWithinColShape](/docs/getelementswithincolshape.md "wikilink") or *false* if a marker wasn't passed to the function.

Code
----

<section name="Function source" class="both" show="true">
``` lua
function getElementsWithinMarker(marker)
    if (not isElement(marker) or getElementType(marker) ~= "marker") then
        return false
    end
    local markerColShape = getElementColShape(marker)
    local elements = getElementsWithinColShape(markerColShape)
    return elements
end
```

</section>
Author: Arran

See Also
--------
