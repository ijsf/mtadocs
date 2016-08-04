This event is triggered when a player leaves the area of a marker created using [createMarker](/createMarker.md "wikilink").

Parameters
----------

``` lua
player leftPlayer, bool matchingDimension
```

-   **leftPlayer**: The player that left the marker's area
-   **matchingDimension**: *true* if the player is in the same dimension as the marker he left

Source
------

The [source](/event_system#Event_source.md "wikilink") of this event is the [marker](/marker.md "wikilink") that the player left.

Example
-------

This example shows a message in the chatbox whenever a player leaves any marker.

``` lua
function markerLeave ( leavingPlayer, matchingDimension )
    outputChatBox ( getPlayerName(leavingPlayer) .. " left a marker" )
end

addEventHandler ( "onClientMarkerLeave", getRootElement(), markerLeave )
```

See Also
--------

### Client marker events

### Client marker functions
