Please use [setPedCanBeKnockedOffBike](/docs/setPedCanBeKnockedOffBike.md "wikilink")

This function controls if you can fall of your bike by accident - namely by banging into a wall.

Syntax
------

``` lua
bool setPlayerCanBeKnockedOffBike ( player thePlayer, bool canBeKnockedOffBike )         
```

### Required Arguments

-   **thePlayer:** the player whose knockoffstatus being changed
-   **state:** the true or false state

Example
-------

This example allows the local player to toggle whether or not he can fall of bikes.

``` lua
function changeCanBeKnockedOff ( command )
    -- The player should enter /knock
    if canPedBeKnockedOffBike ( getLocalPlayer() ) then
        setPlayerCanBeKnockedOffBike ( getLocalPlayer(), false )
        outputChatBox ( "Now you can't be knocked off your bike." )
    else
        setPlayerCanBeKnockedOffBike ( getLocalPlayer(), true )
        outputChatBox ( "Now you can be knocked off your bike." )
    end
end
addCommandHandler ( "knock", changeCanBeKnockedOff )
```

See Also
--------
