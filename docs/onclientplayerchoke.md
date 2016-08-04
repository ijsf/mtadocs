This event is fired when the local player chokes due to the effect of a weapon such as tear gas grenades, fire extinguishers and spray cans.

Parameters
----------

``` lua
int weaponID, ped responsiblePed
```

-   **weapon:** an [int](/docs/int.md "wikilink") representing the ID of the [weapon](/weapon.md "wikilink") which caused the choking.
-   **responsiblePed:** the ped responsible for causing the choking, possiblly nil.

Source
------

The source of this event is the player who is choking. (Local player only)

Cancel effect
-------------

If this event is [canceled](/docs/event_system#canceling.md "wikilink"), the player will not be choked.

Example
-------

<section class="client" name="Client" show="true">
This example disables choking effects from the tear gas grenades.

``` lua
function cancelTearGasChoking(weaponID, responsiblePed)
    if (weaponID==17) then
        cancelEvent()
    end
end
addEventHandler("onClientPlayerChoke", getLocalPlayer(), cancelTearGasChoking)
```

</section>
See Also
--------

### Client player events

### Client event functions
