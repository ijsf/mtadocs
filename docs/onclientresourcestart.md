This event is triggered when a [resource](/docs/resource.md "wikilink") is started. Please note that this is **not** triggered the same time as the serverside event [onResourceStart](/onResourceStart.md "wikilink") is. The event is triggered when any *clientside resources* are started. This means it is triggered when a clientside script is initiated after a download, which includes downloading after join. So:

-   If a resource is running **before** a player joins, the onClientResourceStart event will be triggered after they join and have downloaded that resource.
-   If a resource is started **after** a player has joined, the player will be made to download the required files, and then the onClientResourceStart event will be triggered.

Parameters
----------

``` lua
resource startedResource
```

-   **startedResource**: the [resource](/docs/resource.md "wikilink") that was started.

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the started resource's [root element](/root_element.md "wikilink").

Example
-------

This example outputs name of resource that was started.

``` lua
addEventHandler( "onClientResourceStart", getRootElement( ),
    function ( startedRes )
        outputChatBox( "Resource started: " .. getResourceName( startedRes ) );
    end
);
```

See Also
--------

### Client resource events

### Client event functions
