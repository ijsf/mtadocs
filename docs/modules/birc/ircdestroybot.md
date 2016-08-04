This function is used to destroy a created . After deletion, the ircbot pointer will nolonger be valid. If ircbot is connected, it will be disconnected from the server.

Syntax
------

``` lua
bool ircDestroyBot ( ircbot theBot )
```

### Required Arguments

-   **theBot:** The ircbot which will be destroyed.

### Returns

Returns *true* if ircbot was successfully destroyed, *false* otherwise.

Example
-------

This example creates an ircbot called *DummyBot* on resource start and destroys the bot once the resource has stopped.

``` lua
function resourceStart()
    theBot = ircCreateBot ( "DummyBot" )
end
addEventHandler ( "onResourceStart", getResourceRootElement (), resourceStart )

function resourceStop()
    if theBot then
        ircDestroyBot ( theBot )
    end
end
addEventHandler ( "onResourceStop", getResourceRootElement (), resourceStop )
```

See Also
--------
