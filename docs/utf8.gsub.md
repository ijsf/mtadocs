Returns a copy of the original input string with replaced matches from the pattern by the replacement value.

Syntax
------

``` lua
 )
```

### Required Arguments

-   **input:** A string character sequence
-   **pattern:** A string match [pattern](http://lua-users.org/wiki/PatternsTutorial)
-   **replace:** A string literal OR an integer value OR a function (see examples below) OR a table ({ match = replacement })

### Optional Arguments

-   **match\_limit:** An integer to limit the number of substitutions made

### Returns

Returns a pair of values, the modified *string* and the *integer* number of substitutions made.

Example
-------

<section name="Server" class="server" show="true">
This example shows how to remove color codes from a string and how to uppercase each single character in a string.

``` lua
local text= "#ff0000This text is red"
local colorless = utf8.gsub( text, "#%x%x%x%x%x%x", "" )
print( colorless ) -- This text is red

print( utf8.gsub( "Nice wiki!", ".", utf8.upper ) ) -- NICE WIKI!
```

</section>
<section name="Server" class="server" show="true">
This example uses a table to replace specific words in the input string by an other value.

``` lua
local input = "We have nice weather in London"

local replacements = {
    ["weather"] = "food",
    ["London"] = "Germany"
}

local output = utf8.gsub( input, "%w+", replacements )
print( output ) -- We have nice food in Germany
```

</section>
<section name="Client" class="client" show="true">
This example shows a simple bad word filter, which censors the word 'ugly' in the input string.

``` lua
local input = "You are ugly!"

local badwords = {
    ["ugly"] = true
}

local output = utf8.gsub( input, "%w+",
    function (match)
        local lowerCase = utf8.lower( match )
        
        if badwords[ lowerCase ] then
            return string.rep( '*', utf8.len( match ) )
        end
        
        return match
    end
)

outputConsole( output ) -- You are ****!
```

</section>
See Also
--------
