This function stops a running resource.
**Note:** This function does not stop the resource immediately, so don't expect that it starts stopping until the [onResourceStop](/docs/onresourcestop.md "wikilink") event for that resource is triggered. This happens after the scripts are done executing for this server frame.

Syntax
------

``` lua
bool stopResource ( resource theResource )
```

### Required Arguments

-   **theResource:** the [resource](/docs/resource.md "wikilink") that should be stopped.

### Returns

Returns *true* if the resource was stopped, *false* if the stopping failed, or an invalid resource was passed.

Example
-------

This function stops all running resources except the current one.

``` lua
function stopAllResources()
    -- we store a table of resources
    local allResources = getResources()
    -- for each one of them,
    for i, resource in ipairs(allResources) do
        -- if it's running, and it is not the current resource
        if ( getResourceState(resource) == "running" ) and ( resource ~= getThisResource() ) then
            -- then stop it
            stopResource(resource)
        end
    end
end
```

See Also
--------
