This event is triggered when an element (like a player or vehicle) enters a collision shape.

Parameters
----------

``` lua
colshape theShape, bool matchingDimension
```

-   **theShape:** the colshape that the element entered.
-   **matchingDimension:** *true* if the element is in the same dimension as the colshape, *false* otherwise.

Source
------

The source of this event is the element that entered the colshape.

Example
-------

This example tells player when he/she entered any collision shapes that were created.

``` lua
addEventHandler( "onClientElementColShapeHit", getRootElement( ),
    function ( )
        if ( getElementType( source ) == "player" ) and ( source == getLocalPlayer( ) ) then
            outputChatBox( "You entered colshape" );
        end
    end
);
```

[pl:onClientElementColShapeHit](/docs/pl:onclientelementcolshapehit.md "wikilink")

See Also
--------

### Client element events

### Client event functions
