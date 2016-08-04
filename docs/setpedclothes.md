<lowercasetitle/>

This function allows you set a ped's clothes with just the slot and clothing index, allowing you to forget about texture and model names.

Syntax
------

``` lua
bool setPedClothes(ped thePed, int clothingSlot, int/bool clothingID)
```

### Required Arguments

-   **thePed**: The ped to dress up.
-   **clothingSlot**: The clothing slot to change. See the [clothes catalog](/docs/cj_clothes.md "wikilink") for more info.
-   **clothingID**: The clothing ID to set the slot to, or false to remove clothing from this slot (only applicable to slot IDs &gt; 3). See the [clothes catalog](/docs/cj_clothes.md "wikilink") for more info.

### Returns

This function returns *true* if the clothes were set successfully, *false* otherwise.

Code
----

<section show="true">
``` lua
function setPedClothes(thePed, clothingSlot, clothingID)
    if not isElement(thePed) or type(clothingSlot) ~= "number" then
        error("Invalid arguments to setPedClothes()!", 2)
    end
    
    if not clothingID then
        return removePedClothes(thePed, clothingSlot)
    end
    
    local hasClothes = getPedClothes(thePed, clothingSlot) 
    if hasClothes then
        removePedClothes(thePed, clothingSlot)
    end
    
    local texture, model = getClothesByTypeIndex(clothingSlot, clothingID)
    return addPedClothes(thePed, texture, model, clothingSlot)
end
```

</section>
Example
-------

<section name="Server" class="server" show="true">
This example adds a '/setClothes \[slot\] \[id\]' command.

``` lua
local function clothesCommand(player, slot, id)
    if not tonumber(slot) then
        outputChatBox("SYNTAX: /setClothes [slot] [id]", player, 255, 0, 0)
        return
    end
    
    setPedClothes(player, slot, id)
end
addCommandHandler("setClothes", clothesCommand)
```

</section>
Author: John

See Also
--------
