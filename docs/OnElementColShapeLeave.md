This event is triggered when an player or vehicle element leaves the area of a [colshape](/colshape.md "wikilink").

Parameters
----------

``` lua
colshape theColShape, bool matchingDimension
```

-   **theColShape**: The [colshape](/colshape.md "wikilink") that this element left the area of
-   **matchingDimension**: True if the colshape and the element that left it are in the same dimension

Source
------

The [source](/event_system#Event_source.md "wikilink") of this event is the [player](/player.md "wikilink") or [vehicle](/vehicle.md "wikilink") that left colshape.

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