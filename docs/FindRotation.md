<lowercasetitle></lowercasetitle>

This function takes two sets of XY coordinates. It returns the direction from point A to point B. This can for example be used to make peds face a given point.

Syntax
------

``` lua
float findRotation( float x1, float y1, float x2, float y2 )
```

### Required Arguments

-   **x1**: The X coordinate of the starting point.
-   **y1**: The Y coordinate of the starting point.
-   **x2**: The X coordinate of the target point.
-   **y2**: The Y coordinate of the target point.

Code
----

``` lua
function findRotation( x1, y1, x2, y2 ) 
    local t = -math.deg( math.atan2( x2 - x1, y2 - y1 ) )
    return t < 0 and t + 360 or t
end
```

Example
-------

This command makes the player who enters it face the player whose name is given.

<section name="Server-side example" class="server" show="true">
``` lua
addCommandHandler("facePlayer",function (player, _, targetName)

    local target = getPlayerFromName(targetName); --get player name
    
    if not target then --if there isn't a player
        outputChatBox("Invalid player", player); --output to them and tell them that there's no player
                return; --end the function so nothing else goes through
    end

    local x,y,z     = getElementPosition(player); --get your position
    local tx,ty,tz  = getElementPosition(target); --get the players position
    
    setPedRotation(player, findRotation(x,y,tx,ty) ); --let's set you facing them

end
);
```

</section>
Original function by **Doomed\_Space\_Marine**. Fixed, tested and wiki-fied by **robhol**.

See Also
--------
