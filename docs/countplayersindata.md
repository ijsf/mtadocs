Syntax
------

``` lua
data countPlayerInData ( dataName )
```

### Required Arguments

-   **dataName:** name data to get player in data

### Returns

Return a number of players in the data

Code
----

<section name="Function source" class="client" show="true">
``` lua
function countPlayersInData ( nameData )
 local Players = 0
 for i,plr in ipairs ( getElementsByType ( 'player' ) ) do
 if ( getElementData(plr,nameData) ) then
Players = Players + 1
 end 
 end 
 return Players 
 end
```

</section>
.

Example
-------

<section name="Example" class="client" show="true">
``` lua
addEventHandler('onClientResourceStart',resourceRoot, function ( )
setElementData(localPlayer,'ProWiki',true)
end)

local DataP = countPlayerInData ( 'ProWiki' ) 
outputChatBox(''..DataP..'')
```

</section>
Created By **xiProGamer**.
