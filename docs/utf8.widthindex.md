Returns the location, offset and width of the character at the given location in the UTF-8 string.

Syntax
------

``` lua
 )
```

### Required Arguments

-   **input:** A string character sequence

### Optional Arguments

-   **ambi\_is\_double:** A boolean, if set to *true*, ambiguous character's width is 2 (see example).
-   **default\_width:** An integer, if given, is used as width for unprintable characters.

### Returns

Returns the given location, the offset in UTF-8 encoding (if cursor is in the middle of the wide char - offset will be 2) and the width of the character, otherwise only the location as *integer* will be returned.

Example
-------

<section name="Server" class="server" show="true">
This example

``` lua
local input = "днём"
local raw_width = utf8.width( input, true )

for location = 1, raw_width do
    print( utf8.widthindex( input, location, true ) )
end
```

Output *(enhanced, not raw)*:

| Character | Location | Offset | Width |
|-----------|----------|--------|-------|
| д         | 1        | 1      | 2     |
| д         | 1        | 2      | 2     |
| н         | 2        | 1      | 2     |
| н         | 2        | 2      | 2     |
| ё         | 3        | 1      | 2     |
| ё         | 3        | 2      | 2     |
| м         | 4        | 1      | 2     |
| м         | 4        | 2      | 2     |

</section>
See Also
--------
