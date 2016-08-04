<lowercasetitle/>

This function checks if the [element](/docs/element.md "wikilink") is in a [colshape](/docs/colshape.md "wikilink").

Syntax
------

<section name="Server" class="server" show="true">
``` lua
 colshape / bool isElementWithinAColShape ( element theElement ) 
```

</section>
<section name="Client" class="client" show="true">
``` lua
 ) 
```

</section>
### Required/Optional Arguments

-   **theElement**: The element you want to check. (If not entered in client-side function, local player will be checked instead.)

### Returns

Returns a [colshape](/docs/colshape.md "wikilink") the [element](/docs/element.md "wikilink") is in else false if the element isn't in one or no arguments were passed.

### Code

<section name="Server" class="server" show="true">
``` lua
function isElementWithinAColShape(element)
    if element or isElement(element)then
        for _,colshape in ipairs(getElementsByType("colshape"))do
            if isElementWithinColShape(element,colshape) then
                return colshape
            end
        end
    end
    outputDebugString("isElementWithinAColShape - Invalid arguments or element does not exist",1)
    return false
end
```

</section>
<section name="Client" class="client" show="true">
    function isElementWithinAColShape(element)
        element = element or localPlayer or getLocalPlayer()
        if element or isElement(element)then
            for _,colshape in ipairs(getElementsByType("colshape"))do
                if isElementWithinColShape(element,colshape) then
                    return colshape
                end
            end
        end
        outputDebugString("isElementWithinAColShape - Element does not exist",1)
        return false
    end

</section>
### Example

``` lua
--ToDo
```

See Also
--------
