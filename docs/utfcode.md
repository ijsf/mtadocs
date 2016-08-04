The function returns the UTF codes of the given string.

Syntax
------

``` lua
int utfCode ( string theString )
```

### Required Arguments

-   **theString:** The [string](/docs/string.md "wikilink") to get the UTF code of.

### Returns

Returns an *[int](/docs/int.md "wikilink")* if the function was successful, *false* otherwise.

### Example

<section name="Example" class="both" show="true">
``` lua
local theString = "UTF code"
outputChatBox(utfCode (theString))
```

</section>
See Also
--------
