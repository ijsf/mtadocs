Syntax
------

``` lua
bool getBrowserSource ( browser webBrowser, function callback )
```

### Required arguments

-   **webBrowser:** The browser element you want to get the source of
-   **callback:** a callback function with syntax as described below

#### Callback syntax

``` lua
function ( string code )
```

Returns
-------

Returns *true* if valid arguments have been passed, *false* otherwise.

Example
-------

``` lua
local browser = createBrowser(1024,1024,false,false)      --Create Browser

addEventHandler("onClientBrowserCreated",browser,function()
    loadBrowserURL(browser,"http://www.youtube.com")    --Load URL
end)

addEventHandler("onClientBrowserDocumentReady",browser,function(url)
    local rnt = getBrowserSource(browser,function(code)     --Get Browser Source and Call Function
        outputChatBox(code)                             --Output Code
    end)
    if rnt then
        outputChatBox("Browser Source Got",0,255,0)
    else
        outputChatBox("Failed To Get Browser Source",255,0,0)
    end
end)
```

See Also
--------
