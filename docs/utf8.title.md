Converts a UTF-8 string to title case (uppercase). If *input* is an integer, it is treated as a codepoint and a converted codepoint (integer) is returned.

Syntax
------

``` lua
string utf8.upper ( string|int input )
string utf8.title ( string|int input )
```

### Required Arguments

-   **input:** A string character sequence OR an integer value

### Returns

Returns a *string* in uppercase OR returns an *integer* (see description).

Example
-------

<section name="Client" class="client" show="true">
This example shows how to convert a string to uppercase.

``` lua
local output = utf8.upper( "WHAT ARE YOU UP TO? Do you like uppercase?" )
outputConsole( output ) -- WHAT ARE YOU UP TO? DO YOU LIKE UPPERCASE?

local value = utf8.title( 1088 )
outputConsole( value, type( value ) ) -- 1056, number
```

</section>
See Also
--------
