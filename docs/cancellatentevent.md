Stops a latent event from completing

Syntax
------

<section name="Server" class="server" show="true">
``` lua
bool cancelLatentEvent( player thePlayer, int handle )
```

### Required Arguments

-   **thePlayer:** The player who is receiving the event.
-   **handle:** A handle previous got from [getLatentEventHandles](/docs/getlatenteventhandles.md "wikilink").

</section>
<section name="Client" class="client" show="true">
``` lua
bool cancelLatentEvent( int handle )
```

### Required Arguments

-   **handle:** A handle previous got from [getLatentEventHandles](/docs/getlatenteventhandles.md "wikilink").

</section>
### Returns

Returns a true if the latent event was successfully cancelled, or false if it was not

Example
-------

<section name="Example 1 - 1/2" class="client" show="true">
``` lua
-- Cancel triggerLatentServerEvent directly after execution.
addCommandHandler("cancelLatentEvent",
function ()
    triggerLatentServerEvent("exampleEvent",3000,false,localPlayer)

    -- Get all your active handles, when you executed the command: /cancelLatentEvent
    local handles = getLatentEventHandles() -- Returns a table.

    local handle = handles[#handles] -- Get the latest handle.

    if cancelLatentEvent(handle) then -- Cancel it!
        outputChatBox("Successfully cancelled!",0,200,0)
    end
end)
```

</section>
<section name="Example 1 - 2/2" class="server" show="true">
``` lua
addEvent("exampleEvent",true)
addEventHandler("exampleEvent",root,
function ()
    outputChatBox("Warning! The triggerLatentServerEvent wasn't cancelled!",client,255,0,0) -- warn the user.
end)
```

</section>
<section name="Example 2" class="server" show="true">
``` lua
-- Cancel all my triggerLatentClientEvent's.
addCommandHandler("cancelLatentEvents",
function (player)

    -- Get all active handles from the player that executed the command: /cancelLatentEvents
    local handles = getLatentEventHandles (player) -- Returns a table. 
    
    for index=1,#handles do -- Loop through the table.
        local handle = handles[index]
        cancelLatentEvent(player,handle) -- Cancel it!
    end
end)
```

</section>
<section name="Example 3" class="client" show="true">
``` lua
-- Cancel all my triggerLatentServerEvent's.
addCommandHandler("cancelLatentEvents",
function ()

    -- Get all your active handles, when you executed the command: /cancelLatentEvents
    local handles = getLatentEventHandles () -- Returns a table. 
    
    for index=1,#handles do -- Loop through the table.
        local handle = handles[index] 
        cancelLatentEvent(handle) -- Cancel it!
    end
end)
```

</section>
Requirements
------------

See Also
--------
