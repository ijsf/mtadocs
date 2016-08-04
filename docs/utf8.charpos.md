Converts the UTF-8 codepoint position to byte-string position.

Syntax
------

``` lua
 )
```

### Required Arguments

-   **input:** A string character sequence

### Optional Arguments

-   **charpos:** An integer representing the beginning position (offset will be added/subtracted).
-   **offset:** An integer representing the offset to charpos.

### Returns

Returns the *integer* position as in a byte string and the *integer* codepoint at this position, *nil* otherwise.

Example
-------

<section name="Server" class="server" show="true">
This example takes the second codepoint character and shows the byte-string position and the codepoint character code.

``` lua
local position, codepoint = utf8.charpos( "Привет", 2 )
print( position, codepoint )  -- 3, 1088
```

</section>
<section name="Client" class="client" show="true">
This example extracts the first character by calculating the character length with the UTF8 functions and the inbuilt Lua function string.sub, which processes byte strings.

``` lua
local input = "Привет мир" -- Hello World
local from = utf8.charpos( input, 1 ) -- 1
local to = utf8.charpos( input, 2 ) -- 3

local byteLength = to - from
outputConsole( byteLength ) -- 2

local character = string.sub( input, from, byteLength )
outputConsole( character ) -- П
```

</section>
See Also
--------
