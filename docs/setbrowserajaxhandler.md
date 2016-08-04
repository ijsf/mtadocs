Syntax
------

``` lua
bool setBrowserAjaxHandler ( browser webBrowser, string url [, function handler] )
```

### Required Arguments

-   **webBrowser:** The web browser which will execute the Javascript code
-   **url:** The URL endpoint to handle

### Optional Arguments

-   **handler:** The function to call if the webBrowser attempts to open the ajax endpoint. If this parameter is nil or omitted, the ajax handler for the url will be deleted.

### Additional Information

The handling function (if given), will be called with two tables, representing GET and POST parameters. The handling function may return a string which will be provided to the browser as file content.

Example
-------

This example will output all GET Parameters as well the number of requests made to the ajax endpoint.

``` lua
--In order to render the browser on the full screen, we need to know the dimensions.
local screenWidth, screenHeight = guiGetScreenSize()
 
--Let's create a new browser in local mode. We will not be able to load an external URL.
local webBrowser = createBrowser(screenWidth, screenHeight, true, false)
 
--This is the function to render the browser.
function webBrowserRender()
    --Render the browser on the full size of the screen.
    dxDrawImage(0, 0, screenWidth, screenHeight, webBrowser, 0, 0, 0, tocolor(255,255,255,255), true)
end


local counter = 0
setBrowserAjaxHandler(webBrowser, "ajax.html",
    function(get, post)
        counter = counter+1
        local output = string.format("<pre>You have requested this page %d times.\n", counter)
        -- List Parameters
        local getParameters = "Get Parameters: \n"
        for k, v in pairs(get) do 
            getParameters = getParameters..string.format("[%s] = %s\n", k, v)
        end 
        
        output = output..getParameters.."</pre>"
        return output
    end
);
 
--The event onClientBrowserCreated will be triggered, after the browser has been initialized.
--After this event has been triggered, we will be able to load our URL and start drawing.
addEventHandler("onClientBrowserCreated", webBrowser, 
    function()
        --After the browser has been initialized, we can load our file.
        loadBrowserURL(webBrowser, "http://mta/local/ajax.html?hello=world")
        --Now we can start to render the browser.
        addEventHandler("onClientRender", root, webBrowserRender)
    end
)
```

### Returns

Returns *true* if the ajax handler could be created/removed.

See Also
--------
