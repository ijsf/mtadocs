<lowercasetitle/>

This function is used to determine if an element is within a pickup.

Syntax
------

<section name="Server" class="server" show="true">
``` lua
 bool isElementWithinPickup ( element theElement, pickup thePickup ) 
```

</section>
<section name="Client" class="client" show="true">
``` lua
 ) 
```

</section>
### Required Arguments

-   **theElement:** The [element](/element.md "wikilink") you're checking.
-   **thePickup:** The [pickup](/pickup.md "wikilink") you're checking.

### Returns

Returns *true* if the element is within the pickup, *false* otherwise

### Code

<section name="Function source" class="both" show="true">
``` lua
function isElementWithinPickup(theElement, thePickup)
    if (isElement(theElement) and getElementType(thePickup) == "pickup") then
        local x, y, z = getElementPosition(theElement)
        local x2, y2, z2 = getElementPosition(thePickup)
        if (getDistanceBetweenPoints3D(x2, y2, z2, x, y, z) <= 1) then
            return true
        end
    end
    return false
end
```

</section>
### Example

``` lua
local pickup = createPickup(...)

addCommandHandler("heal", function(source)
    if (isElementWithinPickup(source, pickup)) then
        if (getElementHealth <= 100) then
            setElementHealth(source, 100)
        end
    end
end)
```

See Also
--------
