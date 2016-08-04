Use this function to mute or unmute the player.

Syntax
------

``` lua
bool setPlayerMuted ( player thePlayer, bool state )
```

### Required Arguments

-   **thePlayer:** The [player](/player.md "wikilink") you are muting or unmuting.
-   **state:** Use **true** to mute and **false** to unmute the player.

### Returns

Returns *true* if the player was successfully muted or unmuted, *false* otherwise.

Example
-------

This adds a /mute command that can be used to mute a player.

``` lua
-- create the function
function mutePlayer(player,command,victimName)
    -- if the player has specified a victim name to mute
    if victimName then
        -- get the victim player element from their name
        local victim = getPlayerFromName(victimName)
        -- if the player exists
        if victim then
            -- if they arent already muted
            if ( not isPlayerMuted(victim) ) then
                -- mute them and output a message to the chat
                setPlayerMuted(victim, true)
                outputChatBox("You have been muted.",victim)
            end
        else
            outputChatBox("Could not find player with name: "..tostring(victimName),player)
        end
    else
        outputChatBox("Usage: /mute <player name>",player)
    end
end
-- add the /mute command
addCommandHandler("mute",mutePlayer)
```

See Also
--------
