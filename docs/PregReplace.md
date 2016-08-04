Syntax
------

``` lua
string pregReplace ( string subject, string pattern, string replacement [, int/string flags ] )
```

### Required Arguments

-   **subject:** The input [string](/string.md "wikilink").
-   **pattern:** The pattern [string](/string.md "wikilink") to search for in the input [string](/string.md "wikilink").
-   **replacement:** The replacement [string](/string.md "wikilink") to replace all matches within the input [string](/string.md "wikilink").

### Optional Arguments

-   **flags:** Conjuncted value that contains flags ( 1 - ignorecase, 2 - multiline, 4 - dotall, 8 - extended ) or ( i - Ignore case, m - Multiline, d - Dotall, e - Extended )

### Returns

Returns the replaced *[string](/string.md "wikilink")*, or [bool](/bool.md "wikilink") *false* otherwise.

Example
-------

<section name="Shared ( client and server )" class="both" show="true">
Some examples:

``` lua
addCommandHandler('examples',
    function ()
        -- Replace doh with done
        outputDebugString( pregReplace( 'I doh this, guys.', 'doh', 'done' ) or 'not replaced' ) -- Result: I done this, guys

        -- Remove all uppercase alphabetic characters
        outputDebugString( pregReplace( 'AaaBbbZzz', '[A-Z]{1,}', '' ) or 'not replaced' ) -- Result: aabbzz

        -- Use simple backreference in replacement string
        outputDebugString( pregReplace( "I love Lua!", "(Lua)", "Moon\\1" ) ) -- Result: I love MoonLua!

        -- Remove repeated characters
        outputDebugString( pregReplace( "Keeeeeep this shooooooort.", "((.)\\2{2})\\2+", "\\1" ) ) -- Result: Keeep this shooort.
    end
)
```

</section>
Requirements
------------

See Also
--------
