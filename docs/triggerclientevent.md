This function triggers an event previously registered on a client. This is the primary means of passing information between the server and the client. Clients have a similar [triggerServerEvent](/docs/triggerserverevent.md "wikilink") function that can do the reverse. You can treat this function as if it was an asynchronous function call, using [triggerServerEvent](/docs/triggerserverevent.md "wikilink") to pass back any returned information if necessary.

Almost any data types can be passed as expected, including [elements](/docs/element.md "wikilink") and complex nested [tables](/docs/table.md "wikilink"). Non-element MTA data types like xmlNodes or resource pointers will not be able to be passed as they do not necessarily have a valid representation on the client.

Events are sent reliably, so clients will receive them, but there may be (but shouldn't be) a significant delay before they are received. You should take this into account when using them.

Keep in mind the bandwidth issues when using events - don't pass a large list of arguments unless you really need to. It is marginally more efficient to pass one large event than two smaller ones.

Syntax
------

``` lua
bool triggerClientEvent ( [table/element sendTo=getRootElement()], string name, element sourceElement, [arguments...] )
```

### Required Arguments

-   **name:** The name of the event to trigger client side. You should register this event with [addEvent](/docs/addevent.md "wikilink") and add at least one event handler using [addEventHandler](/docs/addeventhandler.md "wikilink").
-   **sourceElement:** The element that is the [source](/docs/event_system#event_handlers.md "wikilink") of the event.

### Optional Arguments

-   **sendTo:** The event will be sent to all [players](/docs/player.md "wikilink") that are children of the specified element. By default this is the root element, and hence the event is sent to all players. If you specify a single player it will just be sent to that player. This argument can also be a table of player elements.
-   **arguments...:** A list of arguments to trigger with the event. You can pass any lua data type (except functions). You can also pass [elements](/docs/element.md "wikilink").

### Returns

Returns *true* if the event trigger has been sent, *false* if invalid arguments were specified.

Example
-------

### Example 1

This example shows how you can pass a simple “Hello World” message from the server to the all the clients using an event.

<section name="Client" class="client" show="true">
``` lua
function greetingHandler ( message )
    outputChatBox ( "The server says: " .. message )
end
addEvent( "onGreeting", true )
addEventHandler( "onGreeting", localPlayer, greetingHandler )
```

</section>
<section name="Server" class="server" show="true">
``` lua
function greetingCommand ( playerSource, commandName )
    triggerClientEvent ( playerSource, "onGreeting", playerSource, "Hello World!" )
end
addCommandHandler ( "greet", greetingCommand )
```

</section>
When the command “greet” is executed (by typing it in the server console or the player's console), the server's *greetingCommand* function is called. This triggers the client side event *onGreeting* with the string *“Hello World!”*. This event is then handled by the *greetingHandler* function client side which then displays the message.

### Example 2

This example shows how you can pass a simple “Hello World” message from the server to **a single** client using an event.

<section name="Client" class="client" show="true">
``` lua
function greetingHandler ( message )
    outputChatBox ( "The server says: " .. message )
end
addEvent( "onGreeting", true )
addEventHandler( "onGreeting", localPlayer, greetingHandler )
```

</section>
<section name="Server" class="server" show="true">
``` lua
function greetingCommandOne ( playerSource, commandName, playerName )
    if playerName then
        local thePlayer = getPlayerFromName ( playerName )
        if thePlayer then
            triggerClientEvent ( thePlayer, "onGreeting", thePlayer, "Hello World!" )
        else
            -- invalid player name specified
        end
    else
        -- No player name specified
    end 
end
addCommandHandler ( "greet_one", greetingCommandOne )
```

</section>
This works like the first example except an extra *thePlayer* argument is specified for triggerClientEvent.

Changelog
---------

See Also
--------

[ru:triggerClientEvent](/docs/ru:triggerclientevent.md "wikilink")
