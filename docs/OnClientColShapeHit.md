This event is triggered when an physical [element](/element.md "wikilink") hits a [colshape](/colshape.md "wikilink").

**NOTE**: The hit won't be detected if the [element](/element.md "wikilink") that entered the colshape is a colshape or projectile.

Parameters
----------

``` lua
element theElement, bool matchingDimension
```

-   **theElement:** the element that entered the colshape.
-   **matchingDimension:** *true* if theElement is in the same dimension as the colshape, *false* otherwise.

Source
------

The source of this event is the colshape that was hit.

Example
-------

This example outputs “In.” to the chatbox whenever a local user enters a collision shape.

``` lua
function onClientColShapeHit( theElement, matchingDimension )
    if ( theElement == getLocalPlayer() ) then  -- Checks whether the entering element is the local player
        outputChatBox( "In." )  --Outputs.
    end
end
addEventHandler("onClientColShapeHit",getRootElement(),onClientColShapeHit)
```

[pl:onClientColShapeHit](/pl:onClientColShapeHit.md "wikilink")

See Also
--------

### Client colshape events

### Client event functions
