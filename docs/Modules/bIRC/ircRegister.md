This function is used to register an for specified resource. By registering an ircbot for a resource, you are able to use the callbacks called by that bot in that resource.

**Note:** It is required to register your ircbot to the module if you're willing to use callbacks with other resources than the one where specified ircbot was originally created. This function is automatically executed for that specific resource when creating a new ircbot using so registering a newly created ircbot within same resource is not required.

Syntax
------

``` lua
bool ircRegister ( ircbot theBot, [ string resourceName = getResourceName ( getThisResource() ) ] )
```

### Required Arguments

-   **theBot:** The ircbot which you want to call the callbacks.

### Optional Arguments

-   **resourceName:** The name of resource to which the ircbot should be registered. The resource specified must be running. Defaults to current resource's name.

### Returns

Returns *true* if registering callbacks was succesful, *false* otherwise.

Example
-------

This example creates an ircbot called *DummyBot* on when resource **ircecho** starts. *DummyBot* is now able to call the callback function **event\_ircOnText** inside resource **ircecho**.
Once resource **ircecho2** starts, it checks if ircbot named *DummyBot* exists and if it does, it registers that bot's callbacks for resource **ircecho2**. Now *DummyBot* is able to call the callback function **event\_ircOnText** also inside resource **ircecho2**.

<section name="Resource: ircecho" class="server" show="true">
``` lua
function resourceStart()
    theBot = ircCreateBot ( "DummyBot" )
    -- ircRegister ( theBot ) is automatically executed
end
addEventHandler ( "onResourceStart", getResourceRootElement (), resourceStart )

-- This function will be called!
function event_ircOnText ( theBot, channel, sender, message )
    if channel == ircGetName( theBot ) then
        outputServerLog ( "[IRC-ECHO] " .. ircGetName( theBot ) .. " received PM from " .. sender .. ": " .. message )
    else
        outputServerLog ( "[IRC-ECHO] " .. ircGetName( theBot ) .. " received text on " .. channel .. " from " .. sender .. ": " .. message )
    end
end
```

</section>
<section name="Resource: ircecho2" class="server" show="true">
``` lua
function resourceStart()
    if ircGetBotByName ( "DummyBot" ) then
        ircRegister ( ircGetBotByName ( "DummyBot" ) )
    end
end
addEventHandler ( "onResourceStart", getResourceRootElement (), resourceStart )

-- This function wouldn't be called if ircRegister wasn't executed!
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
