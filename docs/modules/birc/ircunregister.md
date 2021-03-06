This function is used to unregister an for a resource. It is the opposite function for .

Syntax
------

``` lua
bool ircUnregister ( ircbot theBot, [ string resourceName = getResourceName ( getThisResource() ) ] )
```

### Required Arguments

-   **theBot:** The ircbot which you want to stop calling the callbacks.

### Optional Arguments

-   **resourceName:** The name of resource from which the ircbot should be unregistered. The resource specified must be running. Defaults to current resource's name.

### Returns

Returns *true* if unregistering callbacks was succesful, *false* otherwise.

Example
-------

This example creates an ircbot called *DummyBot* on when resource **ircecho** starts and makes it unable to call the callback functions inside the resource.

<section name="Resource: ircecho" class="server" show="true">
``` lua
function resourceStart()
    theBot = ircCreateBot ( "DummyBot" )
    ircUnregister ( theBot )
end
addEventHandler ( "onResourceStart", getResourceRootElement (), resourceStart )

-- This callback function will never be called!
function event_ircOnText ( theBot, channel, sender, message )
    if channel == ircGetName( theBot ) then
        outputServerLog ( "[IRC-ECHO] " .. ircGetName( theBot ) .. " received PM from " .. sender .. ": " .. message )
    else
        outputServerLog ( "[IRC-ECHO] " .. ircGetName( theBot ) .. " received text on " .. channel .. " from " .. sender .. ": " .. message )
    end
end
```

</section>
See Also
--------
