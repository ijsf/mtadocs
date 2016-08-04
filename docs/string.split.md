<lowercasetitle></lowercasetitle>

This function splits a string into a table. There is no separator in this function, so all characters will be split no matter what.
If you are looking for a function to split a string from a separator, you should look at [split](/docs/split.md "wikilink").

Syntax
------

``` lua
table string.split( string str )
```

### Required Arguments

-   **str**: The string to split.

### Returns

Returns a table containing the pieces of the split string.

Code
----

<section name="Server- and/or clientside Script" class="both" show="true">
``` lua
function string.split(str)

   if not str or type(str) ~= "string" then return false end

   local splitStr = {}
   for i=1,string.len(str) do
      local char = str:sub( i, i )
      table.insert( splitStr , char )
   end

   return splitStr 
end
```

</section>
Example
-------

<section name="Server" class="server" show="true">
This example splits the string “test string” into a table.

``` lua
local splitStr = string.split( "test string" )
outputDebugString( splitStr[1] ) -- >> "t"
outputDebugString( splitStr[2] ) -- >> "e"
outputDebugString( splitStr[3] ) -- >> "s"
outputDebugString( splitStr[4] ) -- >> "t"
```

</section>
Author: Wafamde

See Also
--------
