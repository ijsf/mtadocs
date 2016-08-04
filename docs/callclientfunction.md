<lowercasetitle/>

This function allows you to call any clientside function from the server's side. Of course only those which are available clientside. It doesn't matter if it's a MTA function, a Lua standard function or a custom function.
Numbers are automatically converted to a string and vice versa clientside to avoid data being lost. If you don't need this feature just delete it.
**Important Note:** Bear in mind that the funcname has to be a **string**! Avoid using callClientFunction in the serverside onResourceStart-event since the client did not add the event handler onServerCallsClientFunction yet.

Syntax
------

``` lua
 )
```

### Required Arguments

-   **client**: The element of the player who should be affected.
-   **funcname**: The name of the function that should be called clientside. May also be a function in a table, e.g. “math.round”.

### Optional Arguments

-   **arg1-argn**: The arguments that should be passed to the function.

Code
----

<section name="Serverside Script" class="server" show="true">
``` lua
function callClientFunction(client, funcname, ...)
    local arg = { ... }
    if (arg[1]) then
        for key, value in next, arg do
            if (type(value) == "number") then arg[key] = tostring(value) end
        end
    end
    -- If the clientside event handler is not in the same resource, replace 'resourceRoot' with the appropriate element
    triggerClientEvent(client, "onServerCallsClientFunction", resourceRoot, funcname, unpack(arg or {}))
end
```

</section>
<section name="Clientside Script" class="client" show="true">
``` lua
function callClientFunction(funcname, ...)
    local arg = { ... }
    if (arg[1]) then
        for key, value in next, arg do arg[key] = tonumber(value) or value end
    end
    loadstring("return "..funcname)()(unpack(arg))
end
addEvent("onServerCallsClientFunction", true)
addEventHandler("onServerCallsClientFunction", resourceRoot, callClientFunction)
```

</section>
Example
-------

<section name="Server" class="server" show="true">
This example sets the player's minute duration.

``` lua
-- define the onPlayerJoin handler function
function onPlayerJoin()
    -- set the minute duration
    callClientFunction(source, "setMinuteDuration", 10000)
end
-- add the event handler
addEventHandler("onPlayerJoin", root, onPlayerJoin)
```

</section>
Author: NeonBlack

See Also
--------
