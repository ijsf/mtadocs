Escapes a string to a UTF-8 format string. It supports several escape formats, see the formatting table.

Syntax
------

``` lua
string utf8.escape ( string input )
```

### Required Arguments

-   **input:** A string character sequence

### Returns

Returns a *string* containing the escaped UTF-8 characters from the original string.

### Formatting

| Format      | Description                                      |
|-------------|--------------------------------------------------|
| **%ddd**    | ddd is a decimal number with variable length     |
| **%{ddd}**  | same as above, but enclosed in brackets          |
| **%uddd**   | same as **%ddd**, 'u' stands for unicode         |
| **%u{ddd}** | same as above, but enclosed in brackets          |
| **%xhhh**   | hexadigit version of **%ddd**                    |
| **%x{hhh}** | same as above, but enclosed in brackets          |
| **%?**      | '?' stands for any other character to be escaped |

Example
-------

<section name="Server" class="server" show="true">
This example escapes two byte-string literals to UTF-8 format by using the utf8.escape function.

``` lua
local output = utf8.escape( "%123 %u123 %{123} %u{123} %xABC %x{ABC}" )
print( output ) -- { { { { ઼ ઼

local output = utf8.escape( "%%123 %? %d %%u" )
print( output ) -- %123 ? d %u
```

</section>
See Also
--------
