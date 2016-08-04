Parameters
----------

``` lua
string url
```

-   **url:** the url of the web page loaded.

Source
------

The [browser](/Element/Browser.md "wikilink") element.

Example
-------

``` lua
addEventHandler ( "onClientBrowserDocumentReady" , root , 
    function ( url ) 
        outputChatBox ( "The page '"  .. url ..  "' has been successfully loaded.") 
    end 
)
```

[pl:onClientBrowserDocumentReady](/pl:onClientBrowserDocumentReady.md "wikilink")

See Also
--------
