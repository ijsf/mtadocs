This function will add an [event](/docs/event.md "wikilink") handler. An event handler is a function that will be called when the event it's attached to is triggered. See [event system](/docs/event_system.md "wikilink") for more information on how the event system works.

Event handlers are functions that are called when a particular event happens. Each event specifies a specific set of variables that are passed to the event handler and can be read by your function. The following global variables are available for use in handler functions:

-   **source**: the element that triggered the event
-   **this**: the element that the event handler is attached to

<!-- -->

-   **client**: the client that triggered the event using [triggerServerEvent](/docs/triggerserverevent.md "wikilink"). Not set if the event was not triggered from a client.

It is important to remember that events pass up and down the [element tree](/docs/element_tree.md "wikilink"). An event triggered on the root element is triggered on every element in the tree. An event triggered on any other element is triggered on its ancestors (its parent element and its parent's parent etc) and its children, grandchildren and great-grandchildren. You can use the *getPropagated* argument to specify if you wish your handler to receive events that have propagated up or down the tree.

The order in which event handlers are triggered is undefined, you should not rely on one event handler being executed before another.

Syntax
------

``` lua
bool addEventHandler ( string eventName, element attachedTo, function handlerFunction, [ bool getPropagated = true, string priority = "normal" ] )    
```

### Required Arguments

-   **eventName:** The name of the [event](/docs/event.md "wikilink") you want to attach the handler function to.
-   **attachedTo:** The [element](/docs/element.md "wikilink") you wish to attach the handler to. The handler will only be called when the event it is attached to is triggered for this element, or one of its children. Often, this can be the root element (meaning the handler will be called when the event is triggered for *any* element).
-   **handlerFunction:** The handler function you wish to call when the event is triggered. This function will be passed all of the event's parameters as arguments, but it isn't required that it takes all of them.

### Optional Arguments

-   **getPropagated:** A boolean representing whether the handler will be triggered if the event was propagated down or up the [element tree](/docs/element_tree.md "wikilink") (starting from the source), and not triggered directly on attachedTo (that is, handlers attached with this argument set to *false* will only be triggered if *source == this*).

### Returns

Returns *true* if the event handler was attached successfully. Returns *false* if the specified event could not be found or any parameters were invalid.

Example
-------

<section name="Server" class="server" show="true">
This serverside example sends a message to everyone in the server when a player spawns.

``` lua
-- get the root element
rootElement = getRootElement()
-- define our handler function
function onPlayerSpawnHandler ( )
    -- get the player's name, source is the player because he was spawned
    local playerName = getPlayerName( source )
    -- output in the chat box that they've spawned
    outputChatBox ( playerName .. " has spawned!" )
end

addEventHandler( "onPlayerSpawn", rootElement, onPlayerSpawnHandler )
```

</section>
Changelog
---------

See Also
--------

[ru:addEventHandler](/docs/ru:addeventhandler.md "wikilink")
