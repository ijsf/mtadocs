The function returns the byte position at specified character position.

Syntax
------

``` lua
int utfSeek ( string theString, int position )
```

### Required Arguments

-   **theString:** The [string](/docs/string.md "wikilink").
-   **position:** An [int](/docs/int.md "wikilink") with the specified charachter position.

### Returns

Returns an *[int](/docs/int.md "wikilink")* if the function was successful, *false* otherwise.

### Example

<section name="Example" class="both" show="true">
``` lua
local teststring = "Hello World"
local testseek = utfSeek ( teststring, 5 )
outputChatBox ( testseek )
```

</section>
See Also
--------
