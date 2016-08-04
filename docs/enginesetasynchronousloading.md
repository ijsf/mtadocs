This function enables or disables asynchronous model loading. Enabling asynchronous model loading may reduce the small pauses that occur when a new model is displayed for the first time. However, it can cause the new models to appear slightly later than they might have otherwise.

Syntax
------

``` lua
bool engineSetAsynchronousLoading ( bool enable, bool force ) 
```

### Required Arguments

-   **enable:** Set to true/false to enable/disable asynchronous loading. Only works if the client's preferences has 'Asynchronous Loading' set to 'Auto'.
-   **force:** If set to true, ignores the client's preferences.

### Returns

Returns *true* if the function executed successfully, *false* otherwise.

Example
-------

The next example enables the model asynchronous loading ignoring client preferences if there are a lot of objects (and the player wants to).

``` lua
addEventHandler("onClientResourceStart", resourceRoot, function()
    if #getElementsByType("object") > 500 then
    engineSetAsynchronousLoading( true, false )
    end
end)
```

How it works
------------

If asynchronous loading is disabled, MTA requests all resources to be loaded at the time they have been requested. This will halt game execution for the time being.

Otherwise, all resource requests are queued up on the to-be-loaded queue. At the beginning of the game frame, the GTA:SA streaming system is updated, along with its streaming slicers. This is when a model is loaded after going through multiple stages. Having asynchronous loading disabled forces all stages to be consecutively run through.

For more details read [GTA:SA Resource Streaming](/docs/gta-sa_resource_streaming.md "wikilink")

See Also
--------
