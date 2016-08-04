Parameters
----------

``` lua
string url, string domain, int reason
```

-   **url**: The blocked URL
-   **domain**: The blocked domain (part of the URL)
-   **reason**: The reason why the resource was blocked. Possibles values:
    -   0: not allowed yet
    -   1: blacklisted
    -   2: blocked protocol scheme

Source
------

The [browser](/docs/Element/Browser.md "wikilink") element

Example
-------

[pl:onClientBrowserResourceBlocked](/docs/pl:onClientBrowserResourceBlocked.md "wikilink")

See Also
--------
