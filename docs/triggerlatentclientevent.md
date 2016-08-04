This function is the same as [triggerClientEvent ](/docs/triggerclientevent_.md "wikilink") except the transmission rate of the data contained in the arguments can be limited and other network traffic is not blocked while the data is being transferred.

Syntax
------

``` lua
bool triggerLatentClientEvent ( [table/element sendTo=getRootElement(),] string name, [int bandwidth=50000,] [bool persist=false,] element theElement, [arguments...] )
```

### Required Arguments

-   **name:** The name of the event to trigger client side. You should register this event with [addEvent](/docs/addevent.md "wikilink") and add at least one event handler using [addEventHandler](/addEventHandler.md "wikilink").
-   **theElement:** The element that is the [source](/docs/event_system#event_handlers.md "wikilink") of the event. This could be another player, or if this isn't relevant, use the root element.

### Optional Arguments

-   **sendTo:** The event will be sent to all [players](/docs/player.md "wikilink") that are children of the specified element. By default this is the root element, and hence the event is sent to all players. If you specify a single player it will just be sent to that player. This argument can also be a table of player elements.
-   **bandwidth:** The bytes per second rate to send the data contained in the arguments.
-   **persist:** A bool indicating whether the transmission should be allowed to continue even after the resource that triggered it has since stopped.
-   **arguments...:** A list of arguments to trigger with the event. You can pass any lua data type (except functions). You can also pass [elements](/docs/element.md "wikilink"). The total amount of data should not exceed 100MB.

### Returns

Returns *true* if the event trigger has been sent, *false* if invalid arguments were specified.

Example
-------

<section name="Client" class="client" show="true">
``` lua
addEvent("onClientReadFile",true)
addEventHandler("onClientReadFile",root,function(data)
    local file = fileCreate("text.txt")                 --Save "data" into "text.txt"
    fileWrite(file,data)
    fileClose(file)
end)
```

</section>
<section name="Server" class="server" show="true">
``` lua
if fileExists("text.txt")
    file = fileOpen("test.txt")                     --Open a file (you can create it yourself).
    local data = fileRead(file,100*1024*1024)               --Max 100 MB
    fileClose(file)                             --Close File
    triggerLatentClientEvent("onClientReadFile",5000,false,root,data)   --trigger
end
```

</section>
Requirements
------------

Changelog
---------

See Also
--------
