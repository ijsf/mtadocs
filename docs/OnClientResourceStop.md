This event is triggered when a [resource](/docs/resource.md "wikilink") is stopped.

Parameters
----------

``` lua
resource stoppedResource
```

-   **stoppedResource**: the [resource](/docs/resource.md "wikilink") that was stopped.

Source
------

The [source](/docs/event_system#Event_source.md "wikilink") of this event is the stopped resource [root element](/root_element.md "wikilink").

Example
-------

This example outputs name of resource that was started.

``` lua
addEventHandler( "onClientResourceStop", getRootElement( ),
    function ( stoppedRes )
        outputChatBox( "Resource stopped: " .. getResourceName( stoppedRes ) );
    end
);
```

See Also
--------

### Client resource events

### Client event functions
