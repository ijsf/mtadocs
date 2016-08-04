This function is used to get the clothes type and index from the texture and model. (Scans through the list of clothes for the specific type).

Syntax
------

``` lua
int int getTypeIndexFromClothes ( string clothesTexture, string clothesModel )
```

### Required Arguments

-   **clothesTexture**: A string determining the clothes texture that you wish to retrieve the type and index from. See the [clothes catalog](/docs/CJ_Clothes.md "wikilink").
-   **clothesModel**: A string determining the corresponding clothes model that you wish to retrieve the type and index from. See the [clothes catalog](/docs/CJ_Clothes.md "wikilink").

Returns
-------

This function returns two integers, type and index respectively, *false* if invalid arguments were passed to the function.

Example
-------

This example gets the current clothes of a certain type on a player, then swaps with the previous in the clothes list.

``` lua
function scriptPreviousClothes ( thePlayer, key, clothesType )
  local currentTexture, currentModel = getPedClothes ( thePlayer, clothesType ) -- get the current clothes on this slot
  local clothesIndex = 1
  if ( currentTexture ) then -- if he had clothes of that type
    local tempA, tempB = getTypeIndexFromClothes ( currentTexture, currentModel ) -- get the type and index for these clothes, so we can decrease and get the previous in the list
    if ( tempA and tempB ) then -- if we found them
      clothesType, clothesIndex = tempA, tempB
    end
  end
  clothesIndex = clothesIndex - 1
  local texture, model = getClothesByTypeIndex ( clothesType, clothesIndex ) -- get the new texture and model
  if ( texture == false ) then -- if we've reached the end of the list
    removePedClothes ( thePlayer, clothesType )
  else addPedClothes ( thePlayer, texture, model, clothesType )
  end
end
addCommandHandler ( "previousClothes", scriptPreviousClothes )
```

See Also
--------
