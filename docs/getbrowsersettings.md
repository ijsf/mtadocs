Syntax
------

``` lua
table getBrowserSettings ()
```

Returns
-------

A table having the following keys:

-   **RemoteEnabled**: *true* if remote websites are enabled, *false* otherwise
-   **RemoteJavascript**: *true* if Javascript is enabled on remote websites, *false* otherwise
-   **PluginsEnabled**: *true* if plugins such as Flash, Silverlight (but not Java) are enabled, *false* otherwise. This setting is *false* by default.

Example
-------

This example is **not tested**

``` lua
local window = guiCreateWindow(200, 200, 1024, 768, "Webbrowser", false)
local browser = guiCreateBrowser(0, 0, 800, 600, false, false, false, window)

for k,v in pairs(getBrowserSettings(browser)) do
 outputChatBox("['"..tostring(k).."'] = '"..tostring(v))
end
```

See Also
--------
