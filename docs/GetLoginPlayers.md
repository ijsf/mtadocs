<lowercasetitle></lowercasetitle>

This function gets all login players in the server

Syntax
------

``` lua
table getLoginPlayers()
```

Code
----

<section name="Function source" class="server" show="true">
``` lua
function getLoginPlayers()
    local loginPlayers = {}
    for _,player in ipairs(getElementsByType("player")) do
        if not isGuestAccount(getPlayerAccount(player)) then
            table.insert(loginPlayers,player)
        end
    end
    return loginPlayers
end
```

</section>
Example
-------

<section name="Example" class="server" show="true">
``` lua
addCommandHandler("loginplayers",
    function (player)
        outputChatBox("- Login Players:",player)
        for _,ply in ipairs(getLoginPlayers()) do
            outputChatBox("- " .. getPlayerName(ply),player)
        end
    end
)
```

</section>
This Function Created By |Mr|-Talal07-|

See Also
--------
