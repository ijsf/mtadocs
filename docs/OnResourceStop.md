This event is triggered when the resource is stopped. This can occur for a number of reasons:

-   The *stop* console command was used
-   The *restart* console command was used
-   The resource was modified (the resource will automatically restart)
-   Another resource stopped it using [stopResource](/stopResource.md "wikilink").

**Note:** If you wish to just detect a single resource being stopped, you should attach handlers for this event to the resource's root element. You can access this using [getResourceRootElement](/getResourceRootElement.md "wikilink").

Parameters
----------

``` lua
resource stoppedResource
```

-   **stoppedResource**: The resource that is being stopped.

Source
------

The [source](/event_system#Event_source.md "wikilink") of this event is the root [element](/element.md "wikilink") of the resource that is being stopped.

Example
-------

This example displays a message in the chatbox when a resource is stopped.

``` lua
addEventHandler ( "onResourceStop", root, 
    function ( resource )
        outputChatBox ( "The Resource " .. getResourceName(resource) .. " was stopped!", root, 255, 255, 255 )
   end 
)
```
