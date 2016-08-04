Returns a string with detailed information of an error.

Syntax
------

``` lua
curlStrerror(curl handler, CURLcode code)
```

Required arguments
------------------

-   **curl** The curl handler
-   **code** The curl code

Returns
-------

The string containing the error, if the code was not found in the system it will return nil

Example
-------

``` lua
curl = curlInit();
if not curl then
    outputDebugString("Can't connect to http://mtasa.com/ with cURL");
else
    curlSetopt(curl, CURLOPT_URL, curlEscape(curl, "http://mtasa.com/"));
    result = curlPerform(curl);
    print(curlStrerror(curl, result)); -- Since we know that mta exists, we sure get the text 'No error.'
    curlClose(curl);
end
```

See also
--------
