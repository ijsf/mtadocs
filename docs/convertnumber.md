This function converts large numbers and adds commas to it. (Example: 100000 -&gt; 100.000)

Syntax
------

``` lua
string convertNumber( int/string number )
```

### Required Arguments

-   **number**: The number to be converted.

### Returns

Returns a string containing the converted number.

Code
----

``` lua
function convertNumber ( number )  
    local formatted = number  
    while true do      
        formatted, k = string.gsub(formatted, "^(-?%d+)(%d%d%d)", '%1,%2')    
        if ( k==0 ) then      
            break   
        end  
    end  
    return formatted
end
```

Example
-------

<section name="Client" class="client" show="true">
This example converts a player's money, and outputs it to the chatbox when they type 'money' into the console:

``` lua
function convertPlayerMoney()
    local pMoney = getPlayerMoney()
    local convertedMoney = convertNumber(pMoney)
    outputChatBox(convertedMoney)
end
addCommandHandler("money", convertPlayerMoney)
```

</section>
See Also
--------
