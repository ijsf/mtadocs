This event is triggered when a player starts to exit a vehicle. This event can be used to cancel exit, if necessary.

Parameters
----------

``` lua
player exitingPlayer, int seat, player jacked, int door
```

-   **exitingPlayer**: A player element representing the player who is starting to exit a vehicle
-   **seat**: An integer representing the seat in which the player is exiting from
-   **jacked**: A player element representing who is jacking

Source
------

The [source](/docs/event_system#Event_source.md "wikilink") of this event is the [vehicle](/vehicle.md "wikilink") in which a player began to exit.

### Canceling

If this event is [canceled](/docs/Event_system_#Canceling.md "wikilink"), the player will not exit the vehicle.

Example
-------

This example locks a player inside a police vehicle if he is a policeman.

``` lua
local policeVehicles = {[598] = true,[596] = true,[597] = true,[599] = true } -- Police vehicle IDs
local policeSkins = {[280] = true,[281] = true,[282] = true,[283] = true,[284] = true,[285] = true,[286] = true } -- Police Skins
 
function exitVehicle ( thePlayer, seat, jacked ) 
   if (policeVehicles[getElementModel (source)]) and (policeSkins[getElementModel(thePlayer)]) then 
      outputChatBox ( "You're the cop! Don't exit the car!", thePlayer )  
      cancelEvent()
   end
end
addEventHandler ( "onVehicleStartExit", getRootElement(), exitVehicle)
```
