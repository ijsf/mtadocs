Enters the character to the [Element/Browser](/docs/element/browser.md "wikilink").

Syntax
------

``` lua
bool injectBrowserCharacter ( browser webBrowser, string character )
```

### Required Arguments

**WebBrowser**

**character**

Example
-------

``` lua
addEventHandler("onClientCharacter", root,
    function(char)
        injectBrowserCharacter(browser, char)
    end
)
```

See also
--------
