This function returns a random string which uses ASCII characters.

Syntax
------

``` lua
int generateRandomASCIIString( int chars )
```

### Required Arguments

-   **chars**: How long the string should be.

Code
----

``` lua
function generateRandomASCIIString(chars)
    local str = ""
    for i = 1, chars do 
        str = str..(string.format("%c", math.random(32, 126)))
    end
    return str
end
```

<i>Author: UnLimiTeD^</i>

<i>Idea by: Poof</i>

Example
-------

``` lua
local str = generateRandomASCIIString(10)
outputChatBox(str)
```

See Also
--------
