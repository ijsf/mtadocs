This function allows you to set a player's camera to follow other elements instead. Currently supported element type is:

-   [Players](/Player.md "wikilink")

Syntax
------

<section name="Server" class="server" show="true">
``` lua
bool setCameraTarget ( player thePlayer [, player target = nil ] )
```

### Required Arguments

-   **thePlayer:** The player whose camera you wish to modify.

### Optional Arguments

-   **target:** The player who you want the camera to follow. If none is specified, the camera will target the player.

**Note:** setCameraTarget will behave strangely if the target you want the camera to follow is inside a vehicle that has hydraulics (upgrade id: 1087) added server sided and if the target is not you.

</section>
<section name="Client 1" class="client" show="true">
``` lua
bool setCameraTarget ( player target )
```

### Required Arguments

-   **target:** The player who you want the local camera to follow.

</section>
### Returns

Returns *true* if the function was successful, *false* otherwise.

Example
-------

This is an example of how one could implement a spectator function. Using the left and right arrow keys you can view other players. Note that this code isn't complete as it doesn't take into account joining or quitting players.

<section class="client" name="Client script" show="true">
``` lua
g_Players = getElementsByType("player")        -- get a list of all players in the server
for i,aPlayer in ipairs(g_Players) do          -- find out what index the local player has in the list
    if aPlayer == localPlayer then
        g_CurrentSpectated = i
        break
    end
end

function spectatePrevious()                    -- decrement the spectate index and spectate the corresponding player
     if g_CurrentSpectated == 1 then
         g_CurrentSpectated = #g_Players
     else
         g_CurrentSpectated = g_CurrentSpectated - 1
     end
    setCameraTarget(g_Players[g_CurrentSpectated])
end

function spectateNext()                        -- increment the spectate index and spectate the corresponding player
     if g_CurrentSpectated == #g_Players then
         g_CurrentSpectated = 1
     else
         g_CurrentSpectated = g_CurrentSpectated + 1
     end
    setCameraTarget(g_Players[g_CurrentSpectated])
end

-- Bind above functions to arrow keys
bindKey("arrow_l", "down", spectatePrevious)
bindKey("arrow_r", "down", spectateNext)
```

</section>
Issues
------

See Also
--------
