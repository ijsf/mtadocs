Syntax
------

``` lua
bool setBrowserVolume ( [browser webBrowser], float volume )
```

### Required Arguments

-   **volume:** A [floating](/float.md "wikilink") point number representing the desired volume level. Range is from **0.0** to **1.0**

### Optional Arguments

-   **webBrowser:** A browser element

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


addCommandHandler ("volume", -- Add command named 'value'
  function (player, command, value)
    if tonumber (value) then -- checking if the value is a number
      setBrowserVolume (theBrowser, value) -- setting the volume value
    else -- if there is no value
      outputChatBox ("You must enter a value.", player)
    end
  end
)
```

See Also
--------
