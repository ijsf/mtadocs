Syntax
------

``` lua
bool toggleObjectRespawn ( object theObject, bool respawn )
```

### Required Arguments

-   **theObject**: the object you want to toggle the respawn from
-   '''respawn *': a bool denoting whether we want to enable (*true*) or disable (*false'') respawning

### Returns

-   *true* when the it was changed successfully.
-   *false* otherwise.

Example
-------

This example adds command *tos* that toggles respawn of all the objects.

``` lua
local respawn = false
addCommandHandler("tos",
    function ()
        for i, object in pairs(getElementsByType("object")) do
            toggleObjectRespawn(object, not respawn)
        end
        outputChatBox("Object respawning " .. (respawn and "disabled" or "enabled"))
        respawn = not respawn
    end)
```

See Also
--------
