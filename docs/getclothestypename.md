This function is used to get the name of a certain clothes type.

Syntax
------

``` lua
string getClothesTypeName ( int clothesType )
```

### Required Arguments

-   **clothesType**: An integer determining the type of clothes you want to get the clothes of.

Returns
-------

This function returns a string (the name of the clothes type) if found, *false* otherwise.

Example
-------

This example is used to output in the chatbox what clothes type the player who uses the 'clothes' command is wearing.

``` lua
function getClothes ( thePlayer, key, clothesType )
  local texture, model = getPedClothes ( source, clothesType )
  if ( texture and model ) then
    outputChatBox ( getPlayerName ( thePlayer ) .. " is wearing " .. texture .. " " .. model .. " on his " .. getClothesTypeName ( clothesType ) )
  end
end
addCommandHandler ( "clothes", getClothes )
```

See Also
--------

[pl:GetClothesTypeName](/docs/pl-getclothestypename.md "wikilink")
