This event is triggered when a player enters a vehicle.

Parameters
----------

``` lua
vehicle theVehicle, int seat, player jacked
```

-   **theVehicle**: A vehicle element representing the vehicle that was entered
-   **seat**: An integer representing the seat in which the player is entering
-   **jacked**: A player element representing a player who has been jacked

Source
------

The [source](/docs/event_system#Event_source.md "wikilink") of this event is the [player](/player.md "wikilink") that entered the vehicle.

Example
-------

**Example 1:** This example forces a player out of a police vehicle if he is not a policeman.

``` lua
policeVehicles = { [598]=true, [596]=true, [597]=true, [599]=true }
policeSkins = { [280]=true, [281]=true, [282]=true, [283]=true, [284]=true, [285]=true, [286]=true }

function enterVehicle ( theVehicle, seat, jacked ) --when a player enters a vehicle
    if ( policeVehicles[getElementModel ( theVehicle )] ) and ( not policeSkins[getElementModel ( source )] ) then -- if the vehicle is one of 4 police cars, and the skin is not a police skin
        removePedFromVehicle ( source ) -- force the player out of the vehicle
        outputChatBox ( "Only policeman can enter police cars!", source ) -- and tell the player why
    end
end
addEventHandler ( "onPlayerVehicleEnter", getRootElement(), enterVehicle ) -- add an event handler for onPlayerVehicleEnter
```

**Example 2:** This example adds a 'moto' helmet to a player when he gets on a nrg bike, and removes it when he gets off.

``` lua
function addHelmetOnEnter ( theVehicle, seat, jacked )
    if ( getElementModel ( theVehicle ) == 522 ) then -- if its a nrg
        addPedClothes ( source, "moto", "moto", 16 ) -- add the helmet
    end
end
addEventHandler ( "onPlayerVehicleEnter", getRootElement(), addHelmetOnEnter )

function removeHelmetOnExit ( theVehicle, seat, jacked )
    if ( getElementModel ( theVehicle ) == 522 ) then -- if its a nrg
        removePedClothes ( source, 16 ) -- remove the helmet
    end
end
addEventHandler ( "onPlayerVehicleExit", getRootElement(), removeHelmetOnExit )
```
