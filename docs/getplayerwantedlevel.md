This function gets a player's current wanted level. The wanted level is indicated by the amount of stars a player has on the GTA HUD.

Syntax
------

<section name="Server" class="server" show="true">
``` lua
int getPlayerWantedLevel ( player thePlayer )
```

### Required Arguments

-   **thePlayer:** The player whose wanted level you wish to get

</section>
<section name="Client" class="client" show="true">
``` lua
int getPlayerWantedLevel ( )
```

</section>
### Returns

Returns an *int* from 0 to 6 representing the player's wanted level, *false* if the player does not exist.

Example
-------

<section name="Example 1: Server" class="server" show="true">
This example finds which players in the server have a wanted level:

``` lua
local players = getElementsByType ( "player" ) -- get a table of all the players in the server
for theKey,thePlayer in ipairs(players) do -- use a generic for loop to step through each player
   local level = getPlayerWantedLevel ( thePlayer ) -- get the wanted level of the player
   if ( level > 0 ) then -- if the player has any stars, announce it in the chat:
      outputChatBox ( getPlayerName ( thePlayer ) .. " has a wanted level of " .. level .. "  stars!" )
   end 
end
```

</section>
<section name="Example 2: Client" class="client" show="true">
This script output your wanted level when you type /wanted.

``` lua
function outputWantedLevel ()
local wantedLvl = getPlayerWantedLevel ( )
   if wantedLvl == 0 then
      outputChatBox ( "You clean", 0, 255, 0)
   else
      outputChatBox ( "You have "..wantedLvl.." wanted stars!", 255, 0, 0)
   end
end
addCommandHandler ( "wanted", outputWantedLevel )
```

</section>
See Also
--------
