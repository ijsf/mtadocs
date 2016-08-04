This function allows you to register a custom [event](/docs/event.md "wikilink"). Custom events function exactly like the built-in events. See [event system](/docs/event_system.md "wikilink") for more information on the event system.

Syntax
------

``` lua
bool addEvent ( string eventName [, bool allowRemoteTrigger = false ] )   
```

### Required Arguments

-   **eventName:** The name of the event you wish to create.

### Optional Arguments

-   **allowRemoteTrigger:** A boolean specifying whether this event can be called remotely using [triggerClientEvent](/docs/triggerclientevent.md "wikilink") / [triggerServerEvent](/docs/triggerserverevent.md "wikilink") or not.

### Returns

Returns *true* if the event was added successfully, *false* if the event was already added.

Example
-------

This example will define a new event called *onSpecialEvent*.

``` lua
-- Add a new event called onSpecialEvent
addEvent ( "onSpecialEvent", true )

-- Define our handler function, that takes a "text" parameter and outputs it to the chatbox
function specialEventHandler ( text )
    outputChatBox ( text )
end

-- Add it as a handler for our event
addEventHandler ( "onSpecialEvent", getRootElement(), specialEventHandler )
```

You can then trigger this event later on using:

``` lua
    triggerEvent ( "onSpecialEvent", getRootElement(), "test" )
```

This will cause the handler to be triggered, so “test” will be output to the chatbox.

See Also
--------

[ru:addEvent](/docs/ru:addevent.md "wikilink")
