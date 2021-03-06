This function is used to set a default setting for a specified [resource](/docs/resource.md "wikilink").

Syntax
------

``` lua
bool setResourceDefaultSetting ( resource theResource, string settingName, string/int/float settingValue )
```

### Required Arguments

-   **theResource:** the resource where the setting is located
-   **settingName:** the name of the default setting
-   **settingValue:** the new value of the setting

### Returns

Returns *true* if the default setting was successfully set, *false* otherwise.

Example
-------

This example checks to see if the server has the freeroam server then sets “spawnmaponstart” to “false”.

``` lua
addEventHandler("onResourceStart",resourceRoot,function()
    local freeroamRes = getResourceFromName("Freeroam")
    if(freeroamRes)then
        setResourceDefaultSetting(freeroamRes,"spawnmaponstart","false")
    end
end)
```

Issues
------

See Also
--------
