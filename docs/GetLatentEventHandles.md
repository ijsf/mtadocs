Gets the currently queued latent events. The last one in the table is always the latest event queued. Each returned handle can be used with [getLatentEventStatus](/getLatentEventStatus.md "wikilink") or [cancelLatentEvent](/cancelLatentEvent.md "wikilink")

Syntax
------

<section name="Server" class="server" show="true">
``` lua
table getLatentEventHandles ( player thePlayer )
```

### Required Arguments

-   **thePlayer:** The player who is receiving the events.

</section>
<section name="Client" class="client" show="true">
``` lua
table getLatentEventHandles ( )
```

</section>
### Returns

Returns a table of handles or false if invalid arguments were passed.

Example
-------

``` lua
TODO
```

Requirements
------------

See Also
--------
