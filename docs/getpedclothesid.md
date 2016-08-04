[Category:Useful\_Functions](/docs/category:useful_functions.md "wikilink") <lowercasetitle/>

This function allows you get a ped's clothing ID, allowing you to forget about texture and model names. <strong>This is intended to overwrite the native getPedClothes function, but has been renamed getPedClothesID here on the wiki. It is also intended to be used in conjunction with [setPedClothes](/docs/setpedclothes.md "wikilink").</strong>

Syntax
------

``` lua
int getPedClothesID(ped thePed, int clothingSlot)
```

### Required Arguments

-   **thePed**: The ped to examine.
-   **clothingSlot**: The clothing slot to examine. See the [clothes catalog](/docs/cj_clothes.md "wikilink") for more info.

### Returns

This function returns the [clothing ID](/docs/cj_clothes.md "wikilink") if successful, false otherwise.

Code
----

<section show="true">
``` lua
function getPedClothesID(thePed, clothingSlot)
    if not isElement(thePed) or type(clothingSlot) ~= "number" then
        error("Invalid arguments to setPedClothes()!", 2)
    end
    
    local texture, model = getPedClothes(thePed, clothingSlot)
    if not texture then
        return false
    else
        local _, id = getTypeIndexFromClothes(texture, model)
        return id
    end
end
```

</section>
Example
-------

<section name="Server" class="server" show="true">
``` lua
-- TODO
```

</section>
Author: John

See Also
--------
