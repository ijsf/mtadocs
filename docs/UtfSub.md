The function returns a sub string, from the specified positions on a character.

Syntax
------

``` lua
string utfSub( string theString, int Start, int End )
```

### Required Arguments

-   **theString:** The [string](/string.md "wikilink").
-   **Start:** An [int](/int.md "wikilink") with the start position.
-   **End:** An [int](/int.md "wikilink") with the end position.

### Returns

Returns a *[string](/string.md "wikilink")* if the function was successful, *false* otherwise.

### Example

<section name="Example" class="both" show="true">
``` lua
local mystring = "Example String"
outputChatBox( utfSub( mystring, 9, 15 ) )
```

</section>
See Also
--------
