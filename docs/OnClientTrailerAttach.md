This event is triggered by a trailer when it gets attached to a towing vehicle.

Parameters
----------

``` lua
vehicle towedBy
```

-   **towedBy:** the vehicle that is now towing the trailer.

Source
------

The source of this event is the trailer that is now being towed.

Example
-------

This example shows on chat name of vehicle, what attach a trailer.

<section name="Client" class="client" show="true">
``` lua
function onAttach(vehicle)
    local name = getVehicleName(vehicle)
    outputChatBox("You were attach the trailer by "..name)
end
addEventHandler("onClientTrailerAttach", getRootElement(), onAttach)
```

</section>
See Also
--------

### Client vehicle events

### Client event functions

[es:onClientTrailerAttach](/docs/es:onClientTrailerAttach.md "wikilink")
