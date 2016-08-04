Converts a UTF-8 string to folded case (lowercase), which can be used to compare two strings. If *input* is an integer, it's treat as a codepoint and a convert codepoint (integer) is returned.

Syntax
------

``` lua
string|int utf8.lower ( string|int input )
string|int utf8.fold ( string|int input )
```

### Required Arguments

-   **input:** A string character sequence OR an integer value

### Returns

Returns a *string* in lowercase OR returns an *integer* (see description).

Example
-------

<section name="Server" class="server" show="true">
This example shows how to convert a string to lowercase, which can be used to compare with other folded strings.

``` lua
local output = utf8.lower( "WHAT ARE YOU UP TO? Do you like uppercase?" )
print( output ) -- what are you up to? do you like uppercase?

local value = utf8.fold( 1088 )
print( type( value ) ) -- number
```

</section>
See Also
--------
