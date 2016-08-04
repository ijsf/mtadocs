Generates a string representing the character codepoints as arguments.

Syntax
------

    string utf8.char ( [ int codepoints... ] )

### Optional Arguments

-   **codepoints:** An variable argument sequence of code points representing the desired unicode characters.

### Returns

Returns a *string* representation of the codepoints passed.

Example
-------

<section name="Server" class="server" show="true">
This example separates an input string into single codepoints and then joins these back together, representing the original input string.

``` lua
local input = "Hello World"
local codepoints = { utf8.byte( input, 1, utf8.len(input) ) }
local joined = utf8.char( unpack(codepoints) )

print( joined ) -- Hello World
```

</section>
<section name="Server" class="server" show="true">
This example takes three code points to generate the string “MTA”.

``` lua
local mta = utf8.char( 77, 84, 65 )
print( mta ) -- MTA
```

</section>
<section name="Client" class="client" show="true">
This example takes the first five code points from the input string and then joins them back together.

``` lua
local input = "Mutli Theft Auto"
local codepoints = {}

-- Extract first 5 characters (read: Mutli)
for index = 1, 5 do
    codepoints[index] = utf8.byte( input, index )
end

local output = ""

-- Join the first 5 characters together
for index = 1, #codepoints do
    output = output .. utf8.char( codepoints[index] )
end

outputConsole( output ) -- Multi
```

</section>
See Also
--------
