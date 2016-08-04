This event is triggered when an element leaves the area of a marker created using [createMarker](/docs/createmarker.md "wikilink").

Parameters
----------

``` lua
element leftElement, bool matchingDimension
```

-   **leftElement**: The element that left the marker's area
-   **matchingDimension**: True if the element is in the same dimension as the marker he left

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [marker](/marker.md "wikilink") that the element left.

Example
-------

This example shows a message in the chat box when element (in this case a player) leaves a marker.

``` lua

local myMarker = createMarker( -2596.6259765625, 579.3583984375, 15.626741409302, "cylinder", 2.0, 255, 0, 0, 150 )

function markerLeave( leaveElement, matchingDimension )
        if getElementType( leaveElement ) == "player" then
          outputChatBox ( "Player has left a marker", getRootElement(), 255, 255, 0 )
        end
end

addEventHandler( "onMarkerLeave", myMarker, markerLeave )
```
