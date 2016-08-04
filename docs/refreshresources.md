This function finds new resources and checks for changes to the current ones.

Syntax
------

``` lua
bool refreshResources ( [ bool refreshAll = false ] )
```

### Optional Arguments

-   **refreshAll**: If *true* MTA will check for changes in all resources. If *false*, MTA will only check for new resources and try to reload resources with errors

**Note:** Checking for changes in all resources can result in lag for a short period of time. It should generally be avoided to set refreshAll to *true*.

### Returns

Returns true is refresh was successful, false otherwise.

Example
-------

<section name="Server" class="server" show="true">
This example will refresh resources when a player uses the /refreshresources command just like the hardcoded /refreshall.

``` lua
function commandRefreshResources(player)
    refreshResources(true)
    outputChatBox("Resources refreshed", player, 255, 255, 0)
end
addCommandHandler("refreshresources", commandRefreshResources)
```

</section>
See Also
--------
