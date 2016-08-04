This event is triggered when an player or vehicle element leaves the area of a [colshape](/docs/colshape.md "wikilink").

Parameters
----------

``` lua
colshape theColShape, bool matchingDimension
```

-   **theColShape**: The [colshape](/docs/colshape.md "wikilink") that this element left the area of
-   **matchingDimension**: True if the colshape and the element that left it are in the same dimension

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [player](/docs/player.md "wikilink") or [vehicle](/docs/vehicle.md "wikilink") that left colshape.

Example
-------

This example prints type of the element which left the created colshape to chatbox.

``` lua
colArea = createColCircle( 1400.0, -700.0, 5.0 ) -- create the colshape

function elementColShapeLeave( colShapeLeft )
    if colShapeLeft == colArea then -- if element left the created colshape
        outputChatBox( getElementType( source ) .. " left the colCircle!" ) -- print the type of the element to chatbox
    end
end
addEventHandler( "onElementColShapeLeave", getRootElement(), elementColShapeLeave ) -- add a handler function for the event
```
