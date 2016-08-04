Escape url's. You wont need this function if you pass the url to curl\_init.

Syntax
------

``` lua
curlEscape(curl handler, string url)
```

Required arguments
------------------

-   **curl** The curl handler
-   **url** The url you want to escape

Returns
-------

The escaped url, if it fails it will return nil

Example
-------

``` lua
curl = curlInit();
if not curl then
    outputDebugString("Can't connect to http://mtasa.com/ with cURL");
else
    curlSetopt(curl, CURLOPT_URL, curlEscape(curl, "http://mtasa.com/"));
    curlClose(curl);
end
```

See also
--------
