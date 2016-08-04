This function is used to remove the current clothes of a certain type on a [ped](/ped.md "wikilink"). It will remove them if the clothesTexture and clothesModel aren't specified, or if they match the current clothes on that slot.

Syntax
------

``` lua
bool removePedClothes ( ped thePed, int clothesType, [ string clothesTexture, string clothesModel ] )
```

### Required Arguments

-   **thePed**: The [ped](/ped.md "wikilink") you want to remove clothes from.
-   **clothesType**: the clothes slot/type to remove. See the [clothes catalog](/CJ_Clothes.md "wikilink").

### Optional Arguments

-   **clothesTexture**: (Server only) A string determining the clothes texture that will be removed. See the [clothes catalog](/CJ_Clothes.md "wikilink").
-   **clothesModel**: (Server only) A string determining the clothes model that will be removed. See the [clothes catalog](/CJ_Clothes.md "wikilink").

Returns
-------

This function returns *true* if the clothes were successfully removed from the ped, *false* otherwise.

Example
-------

<section name="Server" class="server" show="true">
This example adds a 'moto' helmet to a player when he gets on a nrg bike, and removes it when he gets off.

``` lua
function addHelmetOnEnter ( vehicleEntered, seat, jacked )
    if getElementModel ( vehicleEntered ) == 522 then      -- if it's a nrg
        addPedClothes ( source, "moto", "moto", 16 )       -- add the helmet
    end
end
addEventHandler ( "onPlayerVehicleEnter", root, addHelmetOnEnter )

function removeHelmetOnExit ( vehicleExited, seat, jacked )
    if getElementModel ( vehicleExited ) == 522 then       -- if it's a nrg
        removePedClothes ( source, 16, "moto", "moto" )    -- remove that helmet
    end
end
addEventHandler ( "onPlayerVehicleExit", root, removeHelmetOnExit )
```

</section>
See Also
--------

[pl:RemovePedClothes](/pl:RemovePedClothes.md "wikilink")
