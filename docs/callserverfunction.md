<lowercasetitle/> This function allows you to call any serverside function from the client's side. Of course only those which are available serverside. It doesn't matter if it's a MTA function, a Lua standard function or a custom function.
Numbers are automatically converted to a string and vice versa serverside to avoid data being lost. If you don't need this feature just delete it.
**Important Note:** Bear in mind that the funcname has to be a **string**!

Syntax
------

``` lua
 )
```

### Required Arguments

-   **funcname**: The name of the function that should be called serverside. May also be a function in a table, e.g. “math.round”.

### Optional Arguments

-   **arg1-argn**: The arguments that should be passed to the function.

Code
----

<section name="Clientside Script" class="client" show="true">
``` lua
function callServerFunction(funcname, ...)
    local arg = { ... }
    if (arg[1]) then
        for key, value in next, arg do
            if (type(value) == "number") then arg[key] = tostring(value) end
        end
    end
    -- If the serverside event handler is not in the same resource, replace 'resourceRoot' with the appropriate element
    triggerServerEvent("onClientCallsServerFunction", resourceRoot , funcname, unpack(arg))
end
```

</section>
<section name="Serverside Script" class="server" show="true">
``` lua
-- Always, always, always, (always) use a list of allowed servers functions.
-- Otherwise hackers can call any function and destroy your server.
allowedFunctions = { ["setPlayerTeam"]=true, ["getListOfCheese"]=true }

function callServerFunction(funcname, ...)
    if not allowedFunctions[funcname] then
        -- Protect server from abuse
        outputServerLog( "SECURITY: " .. tostring(getPlayerName(client)) .. " tried to use function " .. tostring(funcname) )
        return
    end

    local arg = { ... }
    if (arg[1]) then
        for key, value in next, arg do arg[key] = tonumber(value) or value end
    end
    loadstring("return "..funcname)()(unpack(arg))
end
addEvent("onClientCallsServerFunction", true)
addEventHandler("onClientCallsServerFunction", resourceRoot , callServerFunction)
```

</section>
Example
-------

<section name="Client" class="client" show="true">
This example removes the player from his team.

``` lua
-- get the local player element
local _local = getLocalPlayer()
-- define the leaveTeam command handler function
function cmdLeaveTeam()
    -- set the player's team to nil
    callServerFunction("setPlayerTeam", _local)
end
-- add the command handler
addCommandHandler("leaveTeam", cmdLeaveTeam, false)
```

</section>
Author: NeonBlack

See Also
--------
