Parameters
----------

None

Source
------

The [browser](/docs/element/browser.md "wikilink") element

Example
-------

``` lua
    addEventHandler("onClientBrowserCreated", resourceRoot,
        function ()
                -- when the browser is loaded
        loadBrowserURL(source, "http://mtasa.com") -- load MTA:SA site
        end
    )
```

[pl:onClientBrowserCreated](/docs/pl-onclientbrowsercreated.md "wikilink")

See Also
--------
