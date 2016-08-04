This function checks whether an element is double-sided as set by [setElementDoubleSided](/docs/setElementDoubleSided.md "wikilink") or not.

Syntax
------

``` lua
bool isElementDoubleSided ( element theElement )
```

### Required Arguments

-   **theElement:** The element in which you'd like to check the double-sidedness of.

### Returns

Returns *true* if the **theElement** is double-sided, *false* otherwise.

Example
-------

This example checks if the object created is breakable and if it is then breaks it.

<section name="Server" class="server" show="true">
``` lua
addCommandHandler("createObj",
function(plr, command, id)
    local x, y, z = getElementPosition(plr)
    local object = createObject (id, x, y, z)
    if (isElementDoubleSided(object)) then  -- checks if it is double sided or not
       outputChatBox("The object is double sided", plr)
    else
       outputChatBox("The object is not double sided", plr)
    end
end
)
```

</section>
See Also
--------
