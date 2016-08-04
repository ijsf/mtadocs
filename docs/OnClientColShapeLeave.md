This event triggers whenever an element (a player, a vehicle...) leaves a collision shape.

Parameters
----------

``` lua
element theElement, bool matchingDimension
```

-   **theElement:** the element that left the colshape.
-   **matchingDimension:** *true* if theElement is in the same dimension as the colshape, *false* otherwise.

Source
------

The source of this event is the colshape that the element left.

Example
-------

This example outputs “Out.” to the chatbox whenever a local user leaves a collision shape.

``` lua
function onClientColShapeLeave( theElement, matchingDimension )
    if ( theElement == getLocalPlayer() ) then  -- Checks whether the leaving element is the local player
        outputChatBox( "Out." )  --Outputs.
    end
end
addEventHandler("onClientColShapeLeave",getRootElement(),onClientColShapeLeave)
```

[pl:onClientColShapeLeave](/pl:onClientColShapeLeave.md "wikilink")

See Also
--------

### Client colshape events

### Client event functions
