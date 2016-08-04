This event is fired when a ped is killed due to the effect of a helicopter blades.

Parameters
----------

``` lua
vehicle killer
```

-   **killer:** the vehicle (heli) responsible for causing the death.

Source
------

The source of this event is the ped who was killed

Type
----

This event is a pre reaction event meaning it occurs before any game level reaction to the collision which include:

-   Peds flying off
-   Peds taking damage
-   Blood

Cancel effect
-------------

If this event is [canceled](/docs/Event_system#Canceling.md "wikilink"), the ped will not be killed

Example
-------

<section class="client" name="Client" show="true">
This example disables helicopter killing

``` lua
function cancelDeath()
    cancelEvent()
end
addEventHandler("onClientPedHeliKilled", root, cancelDeath)
```

</section>
Requirements
------------

See Also
--------

### Client ped events

### Client event functions
