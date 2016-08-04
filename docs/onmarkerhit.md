This event is triggered when an element enters a marker created using [createMarker](/docs/createmarker.md "wikilink").

Parameters
----------

``` lua
element hitElement, bool matchingDimension
```

-   **hitElement**: The element that hit the marker
-   **matchingDimension**: True if the element is in the same dimension as the marker he hit

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [marker](/marker.md "wikilink") that got hit by the element.

Example
-------

This example will output a message what type of element has entered a marker.

``` lua

local myMarker = createMarker(-2596.625, 579.358, 15.626, 'cylinder', 2.0, 255, 0, 0, 150) -- create myMarker

function MarkerHit( hitElement, matchingDimension ) -- define MarkerHit function for the handler
    local elementType = getElementType( hitElement ) -- get the hit element's type
    outputChatBox( elementType.." inside myMarker", getRootElement(), 255, 255, 0 ) -- attach the element's type with the text, and output it
end
addEventHandler( "onMarkerHit", myMarker, MarkerHit ) -- attach onMarkerHit event to MarkerHit function
```

Issues
------
