Syntax
------

``` lua
bool injectBrowserMouseDown ( browser webBrowser, string mouseButton )
```

### Required arguments

-   **webBrowser:** The web browser
-   **mouseButton:** The mouse button (Possible values: *left*, *middle*, *right*)

### Returns

Returns *true* if the click was successfully injected, *false* otherwise.

Example
-------

``` lua
addEventHandler("onClientClick", root,
    function(button, state)
    if state == "down" then
        injectBrowserMouseDown(browser, button)
    else
        injectBrowserMouseUp(browser, button)
    end 
end)
```

See also
--------
