This event is triggered when an player or vehicle element collides with a colshape.

Parameters
----------

``` lua
colshape theColShape, bool matchingDimension
```

-   **theColShape**: The [colshape](/colshape.md "wikilink") that this element collided with
-   **matchingDimension**: True if the element and the colshape are in the same dimension

Source
------

The [source](/event_system#Event_source.md "wikilink") of this event is the [player](/player.md "wikilink") or [vehicle](/vehicle.md "wikilink") that collided with the colshape.

Example
-------

This example prints type of the element which entered the created colshape to chatbox.

``` lua
colArea = createColCircle( 1400.0, -700.0, 5.0 ) -- create the colshape

function elementColShapeHit( colShapeHit )
    if colShapeHit == colArea then -- if element entered the created colshape
        outputChatBox( getElementType( source ) .. " entered the colCircle!" ) -- print the type of the element to chatbox
    end
end
addEventHandler( "onElementColShapeHit", getRootElement(), elementColShapeHit ) -- add a handler function for the event
```
