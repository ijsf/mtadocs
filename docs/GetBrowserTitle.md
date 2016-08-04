Syntax
------

``` lua
string getBrowserTitle ( browser webBrowser )
```

### Required arguments

-   **webBrowser:** The browser

### Returns

Returns the title as a [string](/docs/string.md "wikilink"). Returns false if invalid arguments were passed.

Example
-------

``` lua
addCommandHandler("browsers",
    function()
        outputChatBox("List of browser titles:")
        for k, v in pairs( getElementByType("web-browser") ) do
            outputChatBox(k .. ". " .. getBrowserTitle(v))
        end
    end
)
```

See Also
--------
