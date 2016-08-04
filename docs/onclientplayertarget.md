This event is triggered whenever the local player targets an element.

Parameters
----------

``` lua
element target
```

-   **target:** The element the player targetted.

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [player](/docs/player.md "wikilink") that targeted the element.

Example
-------

This example outputs the type of the target the client is aiming at

``` lua
function targetingActivated ( target )
    if ( target ) then
        outputChatBox(tostring(getElementType(target)))
    end
end
addEventHandler ( "onClientPlayerTarget", getRootElement(), targetingActivated )
```

See Also
--------

### Client player events

### Client event functions
