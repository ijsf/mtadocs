This event is triggered when a trailer is detached from a truck.

Parameters
----------

``` lua
vehicle theTruck
```

-   **theTruck**: The truck vehicle that this trailer got detached from.

Source
------

The [source](/event_system#Event_source.md "wikilink") of this event is the trailer [vehicle](/vehicle.md "wikilink") that the truck got detached from.

Example
-------

This example re-attaches a trailer when it detaches.

``` lua
function reattachTrailer(theTruck)
    attachTrailerToVehicle(theTruck, source) -- Reattach the truck and trailer
end

addEventHandler("onTrailerDetach", getRootElement(), reattachTrailer)
```
