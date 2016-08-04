This function restarts a running resource. Restarting will destroy all the elements that the resource has created (as stopping the resource does).

**Note:** This function does not restart the resource immediately. Restarts are queued up until the end of the server's frame to ensure that they occur in the correct order (and that dependent resources can start and stop correctly). The resource being restarted will have an [onResourceStop](/onResourceStop.md "wikilink") event triggered and the restarted instance will receive an [onResourceStart](/onResourceStart.md "wikilink") event. Remember that the element and resource variables will be invalidated during the restart, though of course, the resource's name will not.

Syntax
------

``` lua
bool restartResource ( resource theResource [, bool persistent = false, bool configs = true, bool maps = true, bool scripts = true, bool html = true, bool clientConfigs = true, bool clientScripts = true, bool clientFiles = true ] )
```

### Required Arguments

-   **theResource:** the [resource](/resource.md "wikilink") you want to restart.

### Optional Arguments

-   **persistent:** Unused
-   **configs:** Reload configs?
-   **maps:** Reload maps?
-   **scripts:** Reload (server) scripts?
-   **html:** Reload html files (for resource web access)?
-   **clientConfigs:** Reload client configs?
-   **clientScripts:** Reload client scripts?
-   **clientFiles:** Reload files?

### Returns

Returns *true* if the resource was restarted, *false* if the restart failed, or an invalid resource was passed.

Example
-------

Example 1: This function restarts all running resources.

``` lua
function restartAllResources()
    -- we store a table of resources
    local allResources = getResources()
    -- for each one of them,
    for index, res in ipairs(allResources) do
        -- if it's running,
        if getResourceState(res) == "running" then
            -- then restart it
            restartResource(res)
        end
    end
end
```

Example 2: This example will restart the specify resource every 3600000 milliseconds (hour).

``` lua
setTimer(
    function()  
    --restarting this resource every hour
        restartResource(getThisResource())
    end,
3600000, 0)
```

See Also
--------
