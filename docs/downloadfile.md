Syntax
------

``` lua
bool downloadFile ( string fileName )
```

### Required Arguments

-   **fileName**: A string referencing the name of the file to download

### Returns

Returns *true* if file download has been queued, *false* otherwise.

Example
-------

**Example 1:** This client side event downloads a file when the current resource has started.

``` lua
-- the function is called on resource start
function onThisResourceStart ( )
    downloadFile ( "test.xml" )
end
addEventHandler ( "onClientResourceStart", resourceRoot, onThisResourceStart )
```

See Also
--------
