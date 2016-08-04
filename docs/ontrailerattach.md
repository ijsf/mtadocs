This event is triggered when a trailer is attached to a truck.

Parameters
----------

``` lua
vehicle theTruck
```

-   **theTruck**: The truck vehicle that got attached to this trailer

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the trailer [vehicle](/docs/vehicle.md "wikilink") that the truck got attached to.

Cancel effect
-------------

If this event is [canceled](/docs/event_system#canceling.md "wikilink"), the trailer will detach from the truck again.

Example
-------

This example removes a trailer from the truck it is attached to. Good if you do not want people attaching trailers to vehicles

``` lua
function detachTrailer(theTruck)
    detachTrailerFromVehicle(theTruck, source) --detach the newly attached trailer
 end
addEventHandler("onTrailerAttach", getRootElement(), detachTrailer)
```

[ru:onTrailerAttach](/docs/ru:ontrailerattach.md "wikilink")
