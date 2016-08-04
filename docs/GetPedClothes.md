This function is used to get the current clothes texture and model of a certain type on a [ped](/ped.md "wikilink").

Syntax
------

``` lua
string string getPedClothes ( ped thePed, int clothesType )
```

### Required Arguments

-   **thePed:** The [ped](/ped.md "wikilink") whose clothes you want to retrieve.
-   **clothesType:** The type/slot of clothing you want to get.

### Returns

This function returns 2 *strings*, the clothes texture and model. The first return value will be *false* if this player's clothes type is empty or an invalid player was specified.

Example
-------

<section name="Server" class="server" show="true">
This example prints the model and texture of the current clothing on the player who enters the “clothes” command. For example: “clothes 3” for the shoes.

``` lua
function getClothes ( source, key, clothesType )
    local texture, model = getPedClothes ( source, clothesType )
    if ( texture and model ) then
        outputChatBox ( getPlayerName(source) .. " is wearing " .. texture .. " " .. model ..
                        " on his " .. getClothesTypeName(clothesType), source )
    else
        outputChatBox ( "Invalid input.", source )
    end
end
addCommandHandler ( "clothes", getClothes )
```

</section>
See Also
--------

[pl:GetPedClothes](/pl:GetPedClothes.md "wikilink")
