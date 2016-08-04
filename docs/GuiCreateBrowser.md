Syntax
------

``` lua
 )
```

### Required Arguments

-   **x, y:** The browser's position
-   **width:** The browser's native width
-   **height:** The browser's native height
-   **isLocal:** See examples
-   **isTransparent:** *true* if you want the browser to support transparency, *false* otherwise
-   **isRelative:** This is whether sizes and positioning are relative. If this is true, then all x,y,width,height floats must be between 0 and 1, representing measures relative to the parent.

### Optional Arguments

-   **parent:** This is the parent that the radio button is attached to. If the relative argument is true, sizes and positioning will be made relative to this parent. If the relative argument is false, positioning will be the number of offset pixels from the parent's origin. If no parent is passed, the parent will become the screen - causing positioning and sizing according to screen positioning.

### Returns

Returns *true* if the [gui-browser](/gui-browser.md "wikilink") element was successfully created, *false* otherwise. Returns also *false*, if the user disabled remote pages and *isLocal* was set to *false*.

Example
-------

This examples attached a webbrowser to a CEGUI window, **not is tested**

``` lua
--In order to render the browser on the full screen, we need to know the dimensions.
local screenWidth, screenHeight = guiGetScreenSize()

--Let's create a new browser in remote mode.
local window = guiCreateWindow(0, 0, screenWidth, screenHeight, "Webbrowser", false)
local browser = guiCreateBrowser(0, 0, 800, 600, false, false, false, window)

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
