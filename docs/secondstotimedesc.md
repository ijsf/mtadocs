This function converts plain seconds-integer into a user-friendly time description.

Syntax
------

``` lua
string secondsToTimeDesc ( int seconds )
```

### Required Arguments

-   **seconds**: The integer of seconds to convert into a user-friendly description.

### Returns

Returns a user-friendly-description, or an empty string if the seconds were invalid/negative.

Code
----

``` lua
function secondsToTimeDesc( seconds )
    if seconds then
        local results = {}
        local sec = ( seconds %60 )
        local min = math.floor ( ( seconds % 3600 ) /60 )
        local hou = math.floor ( ( seconds % 86400 ) /3600 )
        local day = math.floor ( seconds /86400 )
        
        if day > 0 then table.insert( results, day .. ( day == 1 and " day" or " days" ) ) end
        if hou > 0 then table.insert( results, hou .. ( hou == 1 and " hour" or " hours" ) ) end
        if min > 0 then table.insert( results, min .. ( min == 1 and " minute" or " minutes" ) ) end
        if sec > 0 then table.insert( results, sec .. ( sec == 1 and " second" or " seconds" ) ) end
        
        return string.reverse ( table.concat ( results, ", " ):reverse():gsub(" ,", " dna ", 1 ) )
    end
    return ""
end
```

**Original Author: MrTasty | Remade by FusioN\_**

Example
-------

<section name="Server-Side Script" class="server" show="true">
in this example we will add the command **/stt seconds** that will show in the chat a user-friendly time description for the command parameter *seconds*.

``` lua
function stt ( thePlayer, command, seconds ) -- create the function
    if ( seconds and tonumber(seconds) ) then -- if the player entered a number (which will be the seconds)
        outputChatBox ( secondsToTimeDesc ( tonumber ( seconds ) ), thePlayer, 0, 255, 0 )
    else -- otherwise, alert him
        outputChatBox ( "Use: /stt [seconds] !", thePlayer, 255, 0, 0 )
    end
end
addCommandHandler ( "stt", stt, false, false )
```

</section>
See Also
--------
