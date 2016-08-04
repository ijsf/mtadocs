This function gets the Z ordering value of a blip. The Z ordering determines if a blip appears on top of or below other blips. Blips with a higher Z ordering value appear on top of blips with a lower value. The default value for all blips is 0.

Syntax
------

``` lua
int getBlipOrdering ( blip theBlip )
```

### Required Arguments

-   **theBlip:** the blip to retrieve the Z ordering value of.

### Returns

Returns the Z ordering value of the blip if successful, *false* otherwise.

Example
-------

``` lua
function getMyBlip(theBlip)
    local ordering = getBlipOrdering ( theBlip )
    if (ordering) then
        outputChatBox("The following blip has a ordering of "..ordering)
    end
end
```

See Also
--------
