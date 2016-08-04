This event is triggered when a player enters a marker created using [createMarker](/createMarker.md "wikilink").

Parameters
----------

``` lua
player hitPlayer, bool matchingDimension
```

-   **hitPlayer:** The player that hit the marker
-   **matchingDimension:** *true* if the player is in the same dimension as the marker he hit

Source
------

The [source](/event_system#Event_source.md "wikilink") of this event is the [marker](/marker.md "wikilink") that got hit by the player.

Example
-------

This code will output a message to the chatbox whenever any player walks into any marker.

``` lua
function MarkerHit ( hitPlayer, matchingDimension )
    outputChatBox ( getPlayerName(hitPlayer) .. " entered a marker" )
end
addEventHandler ( "onClientMarkerHit", getRootElement(), MarkerHit )
```

See Also
--------

### Client marker events

### Client marker functions
