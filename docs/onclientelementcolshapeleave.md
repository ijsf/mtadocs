This event is triggered when an element (like a player or vehicle) leaves a collision shape.

Parameters
----------

``` lua
colshape theShape, bool matchingDimension
```

-   **theShape:** the colshape that the element left.
-   **matchingDimension:** *true* if the element is in the same dimension as the colshape, *false* otherwise.

Source
------

The source of this event is the element that left the colshape.

Example
-------

This example tells player when he/she left any collision shapes that were created.

``` lua
addEventHandler( "onClientElementColShapeLeave", getRootElement( ),
    function ( )
        if ( getElementType( source ) == "player" ) and ( source == getLocalPlayer( ) ) then
            outputChatBox( "You left colshape" );
        end
    end
);
```

[pl:onClientElementColShapeLeave](/docs/pl:onClientElementColShapeLeave.md "wikilink")

See Also
--------

### Client element events

### Client event functions
