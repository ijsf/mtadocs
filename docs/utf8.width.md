Calculates the width of UTF-8 strings with special/unprintable characters, which require special width treatment.

Syntax
------

``` lua
 )
```

### Required Arguments

-   **input:** A string character sequence OR a codepoint integer

### Optional Arguments

-   **ambi\_is\_double:** A boolean, if set to *true*, ambiguous character's width is 2 (see example below).
-   **default\_width:** An integer, if given, is used as width for unprintable characters.

### Returns

Returns the *integer* width of the input string OR the width of the codepoint integer.

Example
-------

<section name="Server" class="server" show="true">
This example shows the difference when *ambi\_is\_double* is set to *false* or *true*.

``` lua
local input = "днём"
local disabled = utf8.width( input, false )
local enabled = utf8.width( input, true )

print( disabled, enabled ) -- 4, 8
```

</section>
See Also
--------
