Closes the curl engine.

Syntax
------

``` lua
curlClose(curl handler)
```

Required arguments
------------------

-   **curl** The curl handler

Returns
-------

True on succes, false otherwise

Example
-------

``` lua
curl = curlInit("http://mtasa.com/");
if not curl then
    outputDebugString("Can't connect to http://mtasa.com/ with cURL");
else
    curlClose(curl);
end
```

See also
--------
