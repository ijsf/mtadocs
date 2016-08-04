This function is used to remove the current clothes of a certain type on a [player](/docs/player.md "wikilink"). It will remove them if the clothesTexture and clothesModel aren't specified, or if they match the current clothes on that slot.

Syntax
------

``` lua
bool removePlayerClothes ( player thePlayer, int clothesType, [ string clothesTexture, string clothesModel ] )
```

### Required Arguments

-   **thePlayer**: The [player](/docs/player.md "wikilink") whose clothes you want to remove.
-   **clothesType**: A integer representing the clothes slot/type to remove. See the [clothes catalog](/docs/cj_clothes.md "wikilink").

### Optional Arguments

-   **clothesTexture**: A string determining the clothes texture that will be removed. See the [clothes catalog](/docs/cj_clothes.md "wikilink").
-   **clothesModel**: A string determining the clothes model that will be removed. See the [clothes catalog](/docs/cj_clothes.md "wikilink").

Returns
-------

This function returns *true* if the clothes were successfully removed from the player, *false* otherwise.

Example
-------

This example adds a 'moto' helmet to a player when he gets on a nrg bike, and removes it when he gets off.

``` lua
function addHelmetOnEnter ( vehicle, seat, jacked )
    if ( getVehicleID ( vehicle ) == 522 ) then            -- if its a nrg
        addPlayerClothes ( source, "moto", "moto", 16 )    -- add the helmet
    end
end
addEventHandler ( "onPlayerVehicleEnter", getRootElement(), addHelmetOnEnter )

function addHelmetOnExit ( vehicle, seat, jacked )
    if ( getVehicleID ( vehicle ) == 522 ) then            -- if its a nrg
        removePlayerClothes ( source, 16, "moto", "moto" ) -- remove that helmet
    end
end
addEventHandler ( "onPlayerVehicleExit", getRootElement(), addHelmetOnExit )
```

See Also
--------
