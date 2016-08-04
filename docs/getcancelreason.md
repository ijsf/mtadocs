Gets the reason for cancelling an event.

Syntax
------

``` lua
string getCancelReason ( )
```

### Required Arguments

*None*

### Returns

Returns the reason that was given with [cancelEvent](/docs/cancelevent.md "wikilink")

Example
-------

This example cancels when a hunterPlayer tries to enter a vehicle and outputs to the world what the player tried to do.

``` lua
-- call 'stopVehicleEntry' whenever hunterPlayer is about to enter a vehicle:
function stopVehicleEntry ( theplayer, seat, jacked )
   cancelEvent (true, "You can't enter a vehicle during war.") -- stop the event from occuring and tell the player the reason.
   outputConsole("We told "..getPlayerName(theplayer).." : "..getCancelReason()) --Now tell everyone what the player tried to do
end
addEventHandler ( "onVehicleStartEnter", huntedPlayer, stopVehicleEntry )
```

See Also
--------
