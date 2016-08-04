This function is used to get the current clothes texture and model of a certain type on a [player](/player.md "wikilink").

Syntax
------

``` lua
string string getPlayerClothes ( player thePlayer, int clothesType )
```

### Required Arguments

-   **thePlayer:** The [player](/player.md "wikilink") whose clothes you want to retrieve.
-   **clothesType:** The type/slot of clothing you want to get.

### Returns

This function returns 2 *strings*, the clothes texture and model. The first return value will be *false* if this player's clothes type is empty or an invalid player was specified.

Example
-------

This example prints the model and texture of the current clothing on the player who calls the 'clothes' command. For example: 'clothes 3' for the shoes.

``` lua
function getClothes ( source, key, clothesType )
    local texture, model = getPlayerClothes ( source, clothesType )
    if ( texture and model ) then
        outputChatBox ( getClientName(source) .. " is wearing " .. texture .. " " .. model ..
                        " on his " .. getClothesTypeName(clothesType), source )
    else
        outputChatBox ( "Invalid input.", source )
    end
end
addCommandHandler ( "clothes", getClothes )
```

See Also
--------
