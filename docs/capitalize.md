<lowercasetitle/>

This function capitalizes a string, so each word has their first letter in uppercase.

Syntax
------

``` lua
string capitalize ( string text )
```

### Required Arguments

-   **text**: A string representing the text you want to capitalize.

### Returns

Returns the *capitalized string* if the conversion was successful, *false* otherwise.

Code
----

``` lua
local function doCapitalizing( substring )
    -- Upper the first character and leave the rest as they are
    return substring:sub( 1, 1 ):upper( ) .. substring:sub( 2 )
end

function capitalize( text )
    -- Sanity check
    assert( type( text ) == "string", "Bad argument 1 @ capitalize [String expected, got " .. type( text ) .. "]")

    -- We don't care about the number of words, so return only the first result string.gsub provides
    return ( { string.gsub( text, "%a+", doCapitalizing ) } )[1]
end
```

Examples
--------

This example capitalizes the below string.

``` lua
capitalize( "testing this cool thing ok" ) -- Result: Testing This Cool Thing Ok
```

See Also
--------
