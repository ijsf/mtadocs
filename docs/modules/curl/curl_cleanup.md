Cleans up the curl handle.

Syntax
------

``` lua
curlCleanup(curl handler)
```

Required arguments
------------------

-   **curl** The curl handler

Returns
-------

Nothing usefull

Example
-------

``` lua
curl = curlInit("http://mtasa.com/");
if not curl then
    outputDebugString("Can't connect to http://mtasa.com/ with cURL");
else
    curlPerform(curl);
    curlCleanup(curl);
    curlClose(curl);
end
```

See also
--------
