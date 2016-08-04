Generates a random sequence of alphanumeric characters.

Syntax
------

``` lua
string generateString ( int length )
```

### Required Arguments

-   **length**: The length of the sequence to generate.

### Returns

Returns a string with the specified length, or false if an invalid length argument was passed.

Code
----

<section name="Client- and/or serverside Script" class="both" show="true">
``` lua
local allowed = { { 48, 57 }, { 65, 90 }, { 97, 122 } } -- numbers/lowercase chars/uppercase chars

function generateString ( len )
    
    if tonumber ( len ) then
        math.randomseed ( getTickCount () )

        local str = ""
        for i = 1, len do
            local charlist = allowed[math.random ( 1, 3 )]
            str = str .. string.char ( math.random ( charlist[1], charlist[2] ) )
        end

        return str
    end
    
    return false
    
end
```

</section>
Example
-------

<section name="Server" class="server" show="true">
This example generates a sequence with 8 characters and outputs it to the chatbox.

``` lua
outputChatBox ( "Generated string was: " .. generateString ( 8 ), root, 0, 255, 0 )
```

</section>
See Also
--------
