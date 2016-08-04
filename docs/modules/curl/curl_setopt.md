Set an curl option.

Syntax
------

``` lua
curlcode curlSetopt(curl handler, curloption option, bool/number/string value)
```

Required arguments
------------------

-   **handler** The curl handler.
-   **option** An curl option, al the options are found [here](/docs/modules/curl/curlopt.md "wikilink")
-   **value** The value, this can be a string, number or boolean. At the [curl option list](/docs/modules/curl/curlopt.md "wikilink") you can find wich option needs a string, number or boolean.

Returns
-------

Returns a curlcode. Nevermind it for now, i even don't know what it is. But it returns it.

Example
-------

``` lua
curl = curlInit("http://mtasa.com/");
if not curl then
    outputDebugString("Can't connect to http://mtasa.com/ with cURL");
else
    curlSetopt(curl, CURLOPT_POST, true);
    curlClose(curl);
end
```

See also
--------
