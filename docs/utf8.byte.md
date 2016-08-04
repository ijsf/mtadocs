Returns the codepoints for the i-th through j-th character of the string passed.

Syntax
------

``` lua
 )
```

### Required Arguments

-   **input:** A string character sequence

### Optional Arguments

-   **i:** An integer representing the beginning position.
-   **j:** An integer representing the ending position.

### Returns

Returns a sequence of *integer* values from the original string if successful, *nil* otherwise.

Example
-------

<section name="Server" class="server" show="true">
This example will print every codepoint in the input string to the server console.

``` lua
local input = "Ницца!"
local codepoints = { utf8.byte( input, 1, utf8.len(input) ) }

for index, codepoint in ipairs( codepoints ) do
    print( "Codepoint @ ".. index .." = ".. codepoint )
end
```

Output:

    Codepoint @ 1 = 1053
    Codepoint @ 2 = 1080
    Codepoint @ 3 = 1094
    Codepoint @ 4 = 1094
    Codepoint @ 5 = 1072
    Codepoint @ 6 = 33

</section>
<section name="Client" class="client" show="true">
This example will print the codepoint of the first character (read: 'M') in the string literal.

``` lua
local first = utf8.byte( "Multi Theft Auto", 1, 1 )
outputConsole( first ) -- 77
```

</section>
See Also
--------
