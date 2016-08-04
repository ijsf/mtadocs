Gets the status of one queued latent event.

Syntax
------

<section name="Server" class="server" show="true">
``` lua
table getLatentEventStatus( player thePlayer, int handle )
```

### Required Arguments

-   **thePlayer:** The player who is receiving the event.
-   **handle:** A handle previous got from [getLatentEventHandles](/getLatentEventHandles.md "wikilink").

</section>
<section name="Client" class="client" show="true">
``` lua
table getLatentEventStatus( int handle )
```

### Required Arguments

-   **handle:** A handle previous got from [getLatentEventHandles](/getLatentEventHandles.md "wikilink").

</section>
### Returns

Returns a table with the following info or false if invalid arguments were passed:

-   **tickStart:** A number estimating how many ticks until the data transfer starts (Negative means the transfer has already started)
-   **tickEnd:** A number estimating how many ticks until the data transfer completes
-   **totalSize:** A number representing how many bytes in total this transfer will transfer
-   **percentComplete:** A number between 0-100 saying how much is done

Example
-------

<section name="Client" class="client" show="true">
The example starts a latent event and outputs the status of the transfer to the client console

``` lua
function beginTransfer()
    triggerLatentServerEvent("blah", resourceRoot, myVeryLongString)    -- Start latent event
    myHandle = getLatentEventHandles()[#getLatentEventHandles()]        -- Get last latent event handle
    myTimer = setTimer( updateStatus, 1000, 0 )                         -- Output status once a second
end

function updateStatus()
    local status = getLatentEventStatus(myHandle)   -- Get latent event status
    if not status then
        killTimer(myTimer)                          -- getLatentEventStatus returns false when the handle is no longer valid
    else
        outputConsole( "Transfer status:"
            .. " tickStart:" .. tostring(status.tickStart)
            .. " tickEnd:" .. tostring(status.tickEnd)
            .. " totalSize:" .. tostring(status.totalSize)
            .. " percentComplete:" .. tostring(status.percentComplete)
            )
    end
end
```

</section>
Requirements
------------

See Also
--------
