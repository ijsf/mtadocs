This function can be used to itinerate through a whole tree without having an element type. useful to get all the elements of a custom map.
\* **NOTE:** This need more testing specially in deeps trees.

Syntax
------

``` lua
table getAllElementsStartingAt(element theStartingElement )
```

### Required Arguments

-   **theStartingElement**: The element where the itineration will start, searching through all the childrens

Code
----

<section name="Function source" class="both" show="true">
``` lua
function getAllElementsStartingAt(startElement)
    local tabla = {}
    for k,v in ipairs(getElementChildren(startElement)) do
        table.insert(tabla,v)
        local childs = getElementChildren(startElement)
        if #childs > 0 then
            for q,w in ipairs(getAllElementsStartingAt(v)) do
                table.insert(tabla,w)
            end
        end
    end
    return tabla
end
```

</section>
Example
-------

This example change all the elements of a whole map to the fifth dimension

``` lua
for k,v in ipairs(getAllElementsStartingAt(mapRoot)) do
    setElementDimension(v,5)
end
```

Author: Gothem

See Also
--------
