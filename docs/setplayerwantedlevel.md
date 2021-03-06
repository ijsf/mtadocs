This function is used to set a player's wanted level. The wanted level is indicated by the amount of stars a player has on the GTA HUD.

Syntax
------

``` lua
bool setPlayerWantedLevel ( player thePlayer, int stars )            
```

### Required Arguments

-   **thePlayer:** The player whose wanted level is to be set
-   **stars:** An integer from 0 to 6 representing the wanted level

### Returns

Returns *true* if the wanted level was set successfully, *false* if any of the arguments were invalid.

Example
-------

This example sets a player's wanted level to six stars if they enter a certain colshape:

``` lua
-- assume that there exists a collision shape named 'policeStation'
function policeStationHit ( thePlayer ) 
   setPlayerWantedLevel ( thePlayer, 6 ) -- set the player's wanted level to 6 stars
   outputChatBox ( getPlayerName ( thePlayer ) .. " entered the police station!" )
end
-- call 'policeStationHit' when a player enters the collision shape:
addEventHandler ( "onColShapeHit", policeStation, policeStationHit )
```

See Also
--------
