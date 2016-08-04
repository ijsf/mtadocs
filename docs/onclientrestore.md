This event is triggered when the local player restores the game screen from a previously minimized state.

Parameters
----------

``` lua
bool didClearRenderTargets
```

-   **didClearRenderTargets:** A bool specifying whether all render targets have been cleared as part of the restore process. Generally, restoring in full screen mode will clear render targets.

Example
-------

This example shows how to cope with life's little upsets

``` lua
function handleRestore( didClearRenderTargets )
    if didClearRenderTargets then
        -- Do any work here to restore render target contents as required
    end
end
addEventHandler("onClientRestore",root,handleRestore)
```

See Also
--------

### Other client events

### Client event functions
