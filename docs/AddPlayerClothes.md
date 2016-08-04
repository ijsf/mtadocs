This function is used to set the current clothes of a certain type on a [player](/player.md "wikilink"). It can only be used on players with the CJ skin (id 0).

Syntax
------

``` lua
bool addPlayerClothes ( player thePlayer, string clothesTexture, string clothesModel, int clothesType )
```

### Required Arguments

-   **thePlayer**: The [player](/player.md "wikilink") whose clothes you want to change.
-   **clothesTexture**: A string determining the clothes texture that will be added. See the [clothes catalog](/CJ_Clothes.md "wikilink").
-   **clothesModel**: A string determining the clothes model that will be added. See the [clothes catalog](/CJ_Clothes.md "wikilink").
-   **clothesType**: A integer representing the clothes slot/type the clothes should be added to. See the [clothes catalog](/CJ_Clothes.md "wikilink").

Returns
-------

This function returns 'true' if the clothes were successfully added to the player, 'false' otherwise.

Example
-------

This example adds a 'moto' helmet to a player when he gets on a nrg bike, and removes it when he gets off.

``` lua
function onEnterVehicle ( theVehicle, seat, jacked )
  if ( getVehicleID ( theVehicle ) == 522 ) then      -- if it's an nrg
    addPlayerClothes ( source, "moto", "moto", 16 )   -- add the helmet
  end
end
addEventHandler ( "onPlayerVehicleEnter", getRootElement(), onEnterVehicle )

function onExitVehicle ( theVehicle, seat, jacked )
  if ( getVehicleID ( theVehicle ) == 522 ) then      -- if it's an nrg
    removePlayerClothes ( source, 16 )                -- remove the helmet
  end
end
addEventHandler ( "onPlayerVehicleExit", getRootElement(), onExitVehicle )
```

See Also
--------
