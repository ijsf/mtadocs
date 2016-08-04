This event is triggered when a [player](/docs/player.md "wikilink") hits a [marker](/marker.md "wikilink").

Parameters
----------

``` lua
marker markerHit, bool matchingDimension
```

-   **markerHit**: The marker the player hit
-   **matchingDimension**: Whether the player and the marker he hit are in the same dimension

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [player](/player.md "wikilink") that hit the marker.

Example
-------

This example outputs when a player hits a marker.

``` lua
function markerAlert(markerHit,matchingDimension)
    if (matchingDimension) then -- Make sure the player is in the same dimension as the marker (so they're actually going into it).
        outputChatBox("You have just entered a marker.",source,255,255,0) -- Output that they are.
    end
end
addEventHandler("onPlayerMarkerHit",getRootElement(),markerAlert)
```
