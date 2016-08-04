Syntax
------

``` lua
table getPlayersInGroup ( string GroupName )
```

### Required Arguments

-   **GroupName**: A string Group Name To Get All Players In It

### Returns

Returns All Players In Groups if it was Argument true , And vice false

Code
----

<section name="Server" class="server" show="true">
``` lua
function getPlayersInGroup ( GroupName )
 
    local aTable = {}
 
    assert ( tostring ( GroupName ) , "Bad Argument At Argument #1 Group Moust String" )
   
    assert ( aclGetGroup ( tostring ( GroupName ) ) , "Bad Argument At Argument #1 Group not Found "  )
   
    for i , player_ in ipairs ( getElementsByType ( "player" ) ) do
   
    local TheAcc =  getPlayerAccount ( player_ )
   
    if not isGuestAccount ( TheAcc ) then  
 
    if isObjectInACLGroup ( "user." ..getAccountName ( TheAcc ) , aclGetGroup ( tostring ( GroupName ) ) ) then
     
    table.insert ( aTable , player_ )
             end  
        end
    end 
    return aTable
end
```

</section>
Example
-------

This example gets Player In Group specific and Kill Players This Group

``` lua
addCommandHandler ( "killPlayerGroup",  
 
function ( _ , _ , GroupName_ )
 
Players = getPlayersInGroup (  GroupName_  )
 
for i , PlayersGroup in ipairs ( Players ) do
 
killPed ( PlayersGroup )
        end
    end
    ) ;
   
-- F8 Say : killPlayerGroup Console
```

Example 2
---------

This example gets Player In Group specific and Give Players Money This Group

``` lua
addCommandHandler("GiveGroupMoney",
 
function ( p , _ , Group_ , aMoney )
 
    Players = getPlayersInGroup ( Group_ )
 
    for i , PlayersGroup in ipairs ( Players ) do
 
    givePlayerMoney ( PlayersGroup , tonumber ( aMoney ) )
 
    end
end
    ) ;
 
--F8 Say : GiveGroupMoney Console 500
```

Author: Abdul\_KariM

skype : kreee89
