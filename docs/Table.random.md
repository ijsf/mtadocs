<lowercasetitle></lowercasetitle>

This function retrieves a random variable from a table.

Syntax
------

``` lua
var table.random( table theTable )
```

### Required Arguments

-   **theTable**: The table you want to get a random variable from.

### Returns

Returns a variable of any type from the table you specified.

Code
----

<section name="Server and Client Side Script" class="both" show="true">
``` lua
function table.random ( theTable )
    return theTable[math.random ( #theTable )]
end
```

</section>
Example 1
---------

<section name="Server" class="server" show="true">
``` lua
-- #Source Function
function table.random ( theTable )
    return theTable[math.random ( #theTable )]
end



local randomGeT = {"1", "2", "3", "4", "5", "6", "7", "8", "9", "10", "11", "12", "13", "14", "15", "16", "17", "18", "19", "20"}

addCommandHandler("random", function()
   local tRandom = table.random(randomGeT) -- randomGeT - The name of the table
   outputChatBox("< "..tRandom.." >")
end)
```

</section>
Credits
-------

-   Original function by The Kid.
-   Modified and simplified by Talidan.
-   Adding Example 1 by Uc.Setllings

See Also
--------
