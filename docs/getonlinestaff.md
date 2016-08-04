Returns all online staff, names separated by two spaces.

Syntax
------

``` lua
table getOnlineStaff()
```

### Required Arguments

-   none \*

Returns
-------

Returns a table populated with player elements who are staff.

``` lua
TABLE = {
   [INTEGER] = ELEMENT
}
```

Code
----

<section name="Server only" class="server" show="true">
``` lua
function getOnlineStaff(removeHEX)
    local players = { };
    for i, v in pairs(getElementsByType'player') do
        if hasObjectPermissionTo(v, 'function.setPlayerMuted',true) then
       table.insert ( players, v);
        end
    end
    return players;
end
```

</section>
Example
-------

<section name="Example" class="server" show="true">
This command makes the player who enters it face the player whose name is given.

``` lua
addCommandHandler( 'staff',
    function( player )
                local staff = {}
                for i, v in pairs(getOnlineStaff()) do
                   staff[i] = getPlayerName(v) or ""
                end
        outputChatBox ( 'Online staff: ' .. table.concat (staff, "\n") )
                outputChatBox ( "Total: " .. #staff, player )
    end
)
```

</section>
See Also
--------
