<lowercasetitle/>

This function returns the ban of the given playername (if the player got banned) otherwise false.
**Important Note:** Case sensitivity of the playername is important!
Example: If 'SomeGuy' got banned, and you will try 'someguy' you will get false.

Syntax
------

``` lua
ban getBanFromName( string playername )
```

### Required Arguments

-   **playername**: The name of the player which got banned.

Code
----

<section name="Server" class="server" show="true">
``` lua
function getBanFromName (name)
    for key, ban in ipairs(getBans()) do -- for every ban do following
        if (getBanNick(ban) == name) then -- if the name of the banned player is equal to our name then
        return ban -- return the ban
    end
    end
    return false -- else return false
end
```

</section>
Example
-------

<section name="Server" class="server" show="true">
This example gets the IP of the ban which has been returned from getBanFromName().

``` lua
addEventHandler("onPlayerBan", root, function(_, banner)
    outputChatBox(("%s has banned %s"):format(getPlayerName(banner), getPlayerName(source)), root, 255, 0, 0)
    local ban = getBanFromName(source:getName())
    local ip = getBanIP(ban) -- Getting the IP of the ban which has been returned from getBanFromName() -- Here you have the ip :)
end)
```

</section>
Author: StiviK

See Also
--------
