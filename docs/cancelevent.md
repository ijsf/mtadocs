This function is used to stop the automatic internal handling of events, for example this can be used to prevent an item being given to a player when they walk over a pickup, by canceling the [onPickupUse](/docs/onpickupuse.md "wikilink") event.

[cancelEvent](/docs/cancelevent.md "wikilink") does not have an effect on all events, see the individual event's pages for information on what happens when the event is canceled. [cancelEvent](/cancelEvent.md "wikilink") does not stop further event handlers from being called, as the order of event handlers being called is undefined in many cases. Instead, you can see if the currently active event has been cancelled using [wasEventCancelled](/wasEventCancelled.md "wikilink").

The use of cancelEvent outside of an event handler has no effect.

If you implement your own custom events and want to handle them being cancelled, you should call [wasEventCancelled](/docs/waseventcancelled.md "wikilink") to check after your call to [triggerEvent](/triggerEvent.md "wikilink").

Syntax
------

<section name="Server" class="server" show="true">
``` lua
bool cancelEvent ( [ bool cancel = true, string reason = "" ] )   
```

</section>
<section name="Client" class="client" show="true">
``` lua
bool cancelEvent ()   
```

</section>
### Optional Arguments

-   **cancel:** True to cancel, false to uncancel.
-   **reason:** The reason for cancelling the event.

### Returns

Always returns *true*.

Example
-------

<section name="Example 1 - Server" class="server" show="true">
This example stops the player *huntedPlayer* from entering a vehicle:

``` lua
-- call 'stopVehicleEntry' whenever hunterPlayer is about to enter a vehicle:
function stopVehicleEntry ( theplayer, seat, jacked )
   cancelEvent () -- stop the event from occuring
end
addEventHandler("onVehicleEnter",getRootElement(),stopVehicleEntry)
```

</section>
<section name="Example 2 - Client" class="client" show="true">
This example prevents any damage to a player clientside by making [cancelEvent](/docs/cancelevent.md "wikilink") an event handler for the [onClientPlayerDamage](/onClientPlayerDamage.md "wikilink") event.

``` lua
addEventHandler ( "onClientPlayerDamage", getRootElement(), cancelEvent )
```

</section>
See Also
--------
