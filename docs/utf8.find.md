Finds the first occurrence of the [pattern](http://lua-users.org/wiki/PatternsTutorial) in the string passed. If an instance of the pattern is found, a pair of values representing the start and the end of the matched string is returned.

Syntax
------

``` lua
 )
```

### Required Arguments

-   **input:** A string character sequence
-   **pattern:** A string match [pattern](http://lua-users.org/wiki/PatternsTutorial) (you can disable pattern matching by using the optional fourth argument *plain*)

### Optional Arguments

-   **startpos:** An integer representing the beginning position.
-   **plain:** A boolean, if pattern matching should be turned off

### Returns

Returns two *number* values for the beginning and ending position of the matched string, *nil* otherwise.

Example
-------

<section name="Server" class="server" show="true">
This example shows how to search for parts of a string.

``` lua
print( utf8.find( "Hello MTA User", "User" ) ) -- 11, 14
print( utf8.find( "Hello MTA User", "e" ) ) -- 2, 2
print( utf8.find( "Hello MTA User", "e", 3 ) ) -- 13, 13
print( utf8.find( "Привет Привет", "%s" ) ) -- 7, 7
print( utf8.find( "Привет Привет", "%s", 1, true ) ) -- nil

-- Comparsion of utf8.find and string.find
local startpos, endpos = utf8.find( "Привет", "и" )
print( startpos, endpos ) -- 3, 3

local startpos, endpos = string.find( "Привет", "и" )
print( startpos, endpos ) -- 5, 6
```

</section>
See Also
--------
