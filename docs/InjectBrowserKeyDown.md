Syntax
------

``` lua
bool injectBrowserKeyDown ( browser webBrowser, string key )
```

### Required arguments

-   **webBrowser:** The web browser
-   **Key:** Key

### Returns

Returns *true* if the key was successfully injected, *false* otherwise.

Example
-------

<section name="Clientside script" class="client" show="true">
    addEventHandler("onClientKey", root,
        function(button, pressedKey)
            if pressedKey then
                injectBrowserKeyDown(browser, button)
            else
                injectBrowserKeyUp(browser, button)
            end
        end
    )

</section>
See also
--------
