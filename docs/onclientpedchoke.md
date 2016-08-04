This event is fired when a ped chokes due to the effect of a weapon such as tear gas grenades, fire extinguishers and spray cans.

Parameters
----------

``` lua
int weaponID, ped responsiblePed
```

-   **weapon:** an [int](/docs/int.md "wikilink") representing the ID of the weapon which caused the choking.
-   **responsiblePed:** the ped responsible for causing the choking, possiblly nil.

Source
------

The source of this event is the ped who is choking.

Cancel effect
-------------

If this event is [canceled](/docs/event_system#canceling.md "wikilink"), the ped will not be choked.

Example
-------

<section class="client" name="Client" show="true">
This example disables choking effects from the tear gas grenades.

``` lua
addEventHandler( "onClientPedChoke", getRootElement( ),
    function ( )
        cancelEvent( );
    end
);
```

</section>
See Also
--------

### Client ped events

### Client event functions
