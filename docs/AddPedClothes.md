This function is used to set the current clothes on a [ped](/ped.md "wikilink").

Syntax
------

``` lua
bool addPedClothes ( ped thePed, string clothesTexture, string clothesModel, int clothesType )
```

### Required Arguments

-   **thePed**: The [ped](/ped.md "wikilink") whose clothes you want to change.
-   **clothesTexture**: A string determining the clothes texture that will be added. See the [clothes catalog](/CJ_Clothes.md "wikilink").
-   **clothesModel**: A string determining the clothes model that will be added. See the [clothes catalog](/CJ_Clothes.md "wikilink").
-   **clothesType**: A integer representing the clothes slot/type the clothes should be added to. See the [clothes catalog](/CJ_Clothes.md "wikilink").

### Returns

This function returns *true* if the clothes were successfully added to the ped, *false* otherwise.

Example
-------

<section name="Server" class="server" show="true">
This example adds a 'moto' helmet to a player when he gets on a nrg bike, and removes it when he gets off.

``` lua
function onEnterVehicle ( theVehicle, seat, jacked )
    if getElementModel ( theVehicle ) == 522 then         -- if it's an nrg
        addPedClothes ( source, "moto", "moto", 16 )   -- add the helmet
    end
end
addEventHandler ( "onPlayerVehicleEnter", root, onEnterVehicle )

function onExitVehicle ( theVehicle, seat, jacked )
    if getElementModel ( theVehicle ) == 522 then      -- if it's an nrg
        removePedClothes ( source, 16 )              -- remove the helmet
    end
end
addEventHandler ( "onPlayerVehicleExit", root, onExitVehicle )
```

</section>
See Also
--------

[pl:AddPedClothes](/pl:AddPedClothes.md "wikilink")
