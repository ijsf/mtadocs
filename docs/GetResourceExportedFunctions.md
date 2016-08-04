Returns a table containing the names of the functions that a resource exports.

Syntax
------

``` lua
table getResourceExportedFunctions ( resource res )
```

### Required Arguments

-   **res:** the resource of which you want to know the exported functions.

### Returns

Returns a table of function names if successful, *false* otherwise.

Example
-------

This simple example will output the names of the functions that the “scoreboard” resource exports.

``` lua
local res = getResourceFromName ( "scoreboard" )
if res then
    local functionNames = getResourceExportedFunctions ( res )
    outputConsole ( "The scoreboard resource exports " .. #functionNames .. " functions:" )
    for i, name in ipairs ( functionNames ) do
        outputConsole ( name )
    end
else
    outputConsole ( "Unable to find the scoreboard resource." )
end
```

See Also
--------
