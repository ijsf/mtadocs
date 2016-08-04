This event is triggered when a player starts to enter a vehicle. This event can be used to cancel entry, if necessary.

Parameters
----------

-   **enteringPlayer**: A player element representing the player who is starting to enter a vehicle
-   **seat**: An integer representing the seat in which the player is entering
-   **jacked**: A player element representing who is going to be jacked
-   

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [vehicle](/vehicle.md "wikilink") in which a player began to enter.

### Canceling

If this event is [canceled](/docs/event_system_#canceling.md "wikilink"), the player will not enter the vehicle.

Example
-------

This example blocks a player out of a police vehicle if he is not a policeman.

``` lua
policeVehicles = { [598]=true,[596]=true,[597]=true,[599]=true }
policeSkins = { [280]=true,[281]=true,[282]=true,[283]=true,[284]=true,[285]=true,[286]=true }

function enterVehicle ( player, seat, jacked ) --when a player enters a vehicle
    if ( policeVehicles[getElementModel(source)] ) and ( not policeSkins[getElementModel(player)] ) then --if the vehicle is one of 4 police cars, and the skin is not a police skin
        cancelEvent()
        outputChatBox ( "Only policeman can enter police cars!", player ) --and tell the player why
    end
end
addEventHandler ( "onVehicleStartEnter", getRootElement(), enterVehicle ) --add an event handler for onVehicleStartEnter
```
