Gets the animation of a player or ped that was set using [setPedAnimation](/docs/setPedAnimation.md "wikilink").

*Note: Use [getPedTask](/docs/getPedTask.md "wikilink") to monitor what movements the player is currently doing.*

Syntax
------

``` lua
string string getPedAnimation ( ped thePed )
```

### Required Arguments

-   **thePed:** the player or ped you want to get the animation of.

### Returns

Returns two *strings*: the first is the name of the block, the second is the name of the animation. Returns *false* if there was an error or if the ped is not doing an animation.

Example
-------

This example adds a command that allows you to copy the animation being used by another player using /copyanim theirName

``` lua
function CopyAnimation(theCommand, thePlayer) -- The Command Function
    if thePlayer then -- If a player name entered then
        thePlayerToCopyFrom = getPlayerFromName(thePlayer) -- get player from his name
        Block, Anim = getPedAnimation(thePlayerToCopyFrom) -- get the player animation
        if Block then -- if got the animation successfully then
            setPedAnimation(localPlayer, Block, Anim) -- set my animation the same
            outputChatBox("* Copied Successfully !") -- output chat message
        end
    else    
        outputChatBox("* Please Enter a Player Name To Copy From !") -- if you didnt entered a player name , then output a chat box message
    end
end
addCommandHandler("copyanim", CopyAnimation) --  adding the Command Handler
```

Example 2
---------

This example shows what block and animation your player is currently performing. Note this will return “N/A” if you did not set an animation with [setPedAnimation](/docs/setPedAnimation.md "wikilink"). If you want to see what the player ped is doing as you control them that is [getPedTask](/getPedTask.md "wikilink").

``` lua
addEventHandler("onClientPreRender",root,
    function ()
    local block, animation = getPedAnimation(localPlayer)
    dxDrawText ( "CURRENT ANIMATION INFO...", 100, 300 )
    if not block then block = "N/A" end
    if not animation then animation = "N/A" end
    dxDrawText ( "Block = "..block.." Animation = "..animation, 100, 315 )
end )
```

See Also
--------
