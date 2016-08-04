<lowercasetitle></lowercasetitle>

This function will give the online admins

Syntax
------

``` lua
table getOnlineAdmins()
```

Code
----

<section name="Function source" class="server" show="true">
``` lua
function getOnlineAdmins()
    local t = {}
    for k,v in ipairs ( getElementsByType("player") ) do
        local acc = getPlayerAccount(v)
        if acc and not isGuestAccount(acc) then
            local accName = getAccountName(acc)
            local isAdmin = isObjectInACLGroup("user."..accName,aclGetGroup("Admin"))
            if isAdmin then
                table.insert(t,v)
            end
        end
    end
    return t
end
```

</section>
Example
-------

<section name="Example" class="server" show="true">
``` lua
addCommandHandler("admins",function(p)
    local Admins = getOnlineAdmins() -- the function will return 1 table
    if #Admins ~= 0 then -- if the admins table not empty then
        outputChatBox("Online Admins",p,255,0,0,true) 
        for k,v in ipairs ( Admins ) do -- loop the table
            outputChatBox("- "..getPlayerName(v),p,255,0,0,true) -- output the player name
        end
    end
end )
```

</section>
Function created by **Al3grab**.

See Also
--------
