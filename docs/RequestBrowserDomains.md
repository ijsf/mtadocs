Syntax
------

``` lua
 )
```

### Required Arguments

-   **pages:** A table containing all domains

### Optional Arguments

-   **parseAsURL:** *true* if the passed addresses should be converted from URLs, *false* otherwise.
-   **callback:** A callback function that is called as soon as the result is available

Syntax:

``` lua
function(bool wasAccapted, table new_domains)
```

### Returns

Returns **true**, if the string was successfully read, **false** otherwise.

Example
-------

``` lua
requestBrowserDomains({ "mtasa.com" }) -- request browser domain
showCursor(true) -- show cursor
addEventHandler("onClientBrowserWhitelistChange", root,
   function(newDomains)
     if newDomains[1] == "mtasa.com" then
       local browser = createBrowser(1280, 720, false, false) -- create browser
       loadBrowserURL(browser, "http://mtasa.com/") -- load browser url
   end
end
)
```

See also
--------
