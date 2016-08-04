Returns a substring of the string passed. The substring starts at *i*. If the third argument *j* is not given, the substring will end at the end of the string. If the third argument is given, the substring ends at and includes *j*.

Syntax
------

``` lua
 )
```

### Required Arguments

-   **input:** A string character sequence

### Optional Arguments

-   **i:** An integer representing the beginning position (may be negative).
-   **j:** An integer representing the ending position (may be negative).

### Returns

Returns a *string* substring of the original string, containing the selected range from the original string.

Example
-------

<section name="Client" class="client" show="true">
This example shows how to extract a substring from a UTF-8 string.

``` lua
local input = "Yarın Salı"

local output = utf8.sub( input, 1, 4 )
outputConsole( output ) -- Yarı

local output = utf8.sub( input, -4 )
outputConsole( output ) -- Salı

local output = utf8.sub( input, -4, -1 )
outputConsole( output ) -- Salı
```

</section>
See Also
--------
