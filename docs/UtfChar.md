The function returns the string of the specified UTF code.

Syntax
------

``` lua
string utfChar ( int characterCode )
```

### Required Arguments

-   **characterCode:** The UTF code, to get the string of.

### Returns

Returns a *[string](/string.md "wikilink")* if the function was successful, *false* otherwise.

### Example

<section name="Example" class="both" show="true">
``` lua
local Char = utfChar(65)
outputChatBox(Char) -- Result : A
```

</section>
See Also
--------
