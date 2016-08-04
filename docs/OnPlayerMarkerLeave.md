This event is triggered when a [player](/player.md "wikilink") leaves the area of a [marker](/marker.md "wikilink").

Parameters
----------

``` lua
marker markerLeft, bool matchingDimension
```

-   **markerLeft**: The marker the player left
-   **matchingDimension**: Whether the player and the marker he left are in the same dimension

Source
------

The [source](/event_system#Event_source.md "wikilink") of this event is the [player](/player.md "wikilink") that left the marker.

Example
-------

This example will output the name of the player that has left a specific marker to the chatbox.

``` lua
-- Create our marker
marker = createMarker(1248,2012,123,"corona",7,255,255,255,255)

function someoneLeftMarker(markerLeft,matchingDimension)
   -- Output our message
   outputChatBox(getPlayerName(source).." has left the marker!",getRootElement(),255,0,0)
end
-- Add an event handler to trigger our function
addEventHandler("onPlayerMarkerLeave",marker,someoneLeftMarker)
```
