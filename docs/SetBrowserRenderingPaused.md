Syntax
------

``` lua
bool setBrowserRenderingPaused ( browser webBrowser, bool paused )
```

### Required Arguments

-   **webBrowser:** The browser
-   **paused:** *true* to pause rendering, *false* to continue

### Returns

Returns *true* if the state was successfully changed

Example
-------

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


addCommandHandler ("pause", -- Add command named 'pause'
  function (player, command, value)
    if (value) then -- checking for a value
      setBrowserRenderingPaused (theBrowser, value) 
    else -- if there is no value
      outputChatBox ("You must enter a value.", player)
    end
  end
)
```

See also
--------
