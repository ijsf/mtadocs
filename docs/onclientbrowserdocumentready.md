Parameters
----------

``` lua
string url
```

-   **url:** the url of the web page loaded.

Source
------

The [browser](/docs/element/browser.md "wikilink") element.

Example
-------

``` lua
addEventHandler ( "onClientBrowserDocumentReady" , root , 
    function ( url ) 
        outputChatBox ( "The page '"  .. url ..  "' has been successfully loaded.") 
    end 
)
```

[pl:onClientBrowserDocumentReady](/docs/pl-onclientbrowserdocumentready.md "wikilink")

See Also
--------
