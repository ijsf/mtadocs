<lowercasetitle></lowercasetitle>

This function find in name map \[DM\] For Race.

Syntax
------

``` lua
bool isMapDM()
```

### Required Arguments

-   none.

### Returns

Returns *true* if the [map](/map.md "wikilink") find in name \[DM\] , *false* if not find in name map \[DM\] .

Code
----

<section name="Server" class="server" show="true">
``` lua
function isMapDM()
   if getMapName():upper():find("[DM]") or getMapName():upper():find("=DM=") or getMapName():upper():find("DM") then
        return true
    else
        return false
    end
end
```

</section>
Example
-------

This example will check in name map \[DM\].

<section name="Server" class="server" show="true">
``` lua
addCommandHandler("show",function(player)
if ( isMapDM() ) then
outputChatBox("This Map DM",player,255,0,0,true)
end
end)
```

</section>
Author: AboShanab.

See Also
--------
