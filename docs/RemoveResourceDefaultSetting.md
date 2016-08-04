This function is used to remove a default setting from specified [resource](/docs/resource.md "wikilink").

Syntax
------

``` lua
bool removeResourceDefaultSetting ( resource theResource, string settingName ) 
```

### Required Arguments

-   **theResource:** the resource which setting is to be removed
-   **settingName:** name of the default setting which is to be removed

### Returns

Returns *true* if the default setting was successfully removed, *false* otherwise.

Example
-------

This example would check if the server has the freeroam resource and removes the default settings called “spawnmaponstart”.

``` lua
addEventHandler("onResourceStart",resourceRoot,function()
    local freeroamRes = getResourceFromName("Freeroam")
    if(freeroamRes)then
        removeResourceDefaultSetting(freeroamRes,"spawnmaponstart")
    end
end)
```

Issues
------

See Also
--------
