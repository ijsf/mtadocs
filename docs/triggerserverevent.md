This function triggers an event previously registered on the server. This is the primary means of passing information between the client and the server. Servers have a similar [triggerClientEvent](/docs/triggerclientevent.md "wikilink") function that can do the reverse. You can treat this function as if it was an asynchronous function call, using [triggerClientEvent](/docs/triggerclientevent.md "wikilink") to pass back any returned information if necessary.

Almost any data types can be passed as expected, including [elements](/docs/element.md "wikilink") and complex nested [tables](/docs/table.md "wikilink"). Non-element MTA data types like xmlNodes or resource pointers will not be able to be passed as they do not necessarily have a valid representation on the client.

Events are sent reliably, so the server will receive them, but there may be (but shouldn't be) a significant delay before they are received. You should take this into account when using them.

Keep in mind the bandwidth issues when using events - don't pass a large list of arguments unless you really need to. It is marginally more efficient to pass one large event than two smaller ones.

Syntax
------

``` lua
bool triggerServerEvent ( string event, element theElement, [arguments...] )
```

### Required Arguments

-   **event:** The name of the event to trigger server-side. You should register this event with [addEvent](/docs/addevent.md "wikilink") and add at least one event handler using [addEventHandler](/docs/addeventhandler.md "wikilink").
-   **theElement:** The element that is the [source](/docs/event_system#event_handlers.md "wikilink") of the event.

### Optional Arguments

-   **arguments...:** A list of arguments to trigger with the event. You can pass any lua data type (except functions). You can also pass [elements](/docs/element.md "wikilink").

### Returns

Returns *true* if the event trigger has been sent, *false* if invalid arguments were specified or a client side element was a parameter.

Example
-------

This example shows how you can pass a simple “Hello World” message from the client to the server using an event.

<section name="Server" class="server" show="true">
``` lua
function greetingHandler ( message )
    -- the predefined variable 'client' points to the player who triggered the event and should be used due to security issues   
    outputChatBox ( "The client says: " .. message, client )
end
addEvent( "onGreeting", true )
addEventHandler( "onGreeting", resourceRoot, greetingHandler ) -- Bound to this resource only, saves on CPU usage.
```

</section>
<section name="Client" class="client" show="true">
``` lua
function greetingCommand ( commandName )
    triggerServerEvent ( "onGreeting", resourceRoot, "Hello World!" )
    -- Source can be this resource as it saves on CPU and prevents event name conflicts with other resources but you can't use resourceRoot if another resource will handle the event.
end
addCommandHandler ( "greet", greetingCommand )
```

</section>
When the command “greet” is executed (by typing it in the server console or the player's console), the clients *greetingCommand* function is called. This triggers the server-side event *onGreeting* with the string *“Hello World!”*. This event is then handled by the *greetingHandler* function server-side which then displays the message.

See Also
--------

[ru:triggerServerEvent](/docs/ru:triggerserverevent.md "wikilink")
