Syntax
------

``` lua
browser guiGetBrowser ( gui-browser theBrowser )
```

### Required Arguments

-   **theBrowser:** The gui-browser

### Returns

Returns the [Browser](/docs/element/browser.md "wikilink") element if a correct [gui-browser](/Element/gui-browser.md "wikilink") has been passed, *false* otherwise.

Example
-------

This examples get's browser element from gui-browser and attach a webbrowser to a CEGUI window.

``` lua
--In order to render the browser on the full screen, we need to know the dimensions.
local screenWidth, screenHeight = guiGetScreenSize()

--Let's create a new browser in remote mode.
local window = guiCreateWindow(200, 200, 1024, 768, "Webbrowser", false)
local browser = guiCreateBrowser(0, 0, 800, 600, false, false, window)

-- The event onClientBrowserCreated will be triggered, after the browser has been initialized.
-- After this event has been triggered, we will be able to load our URL
local theBrowser = guiGetBrowser(browser) -- Get the browser element from gui-browser
addEventHandler("onClientBrowserCreated", theBrowser, 
    function()
        -- After the browser has been initialized, we can load www.youtube.com
        loadBrowserURL(source, "http://www.youtube.com")
    end
)
```

See Also
--------
