This will change the text of a player's nickname in the world to something besides the nickname he chose. This will not change the player's actual nickname, it only changes the visible aspect inside the world (you will see his original nickname in the scoreboard and will refer to his original name in scripts).

Syntax
------

``` lua
bool setPlayerNametagText ( player thePlayer, string text )
```

### Required Arguments

-   **thePlayer:** The player whose nickname text you wish to change
-   **text:** The new nickname text that will be displayed

### Returns

Returns *true* if successful, *false* otherwise.

Example
-------

<section name="Server" class="server" show="true">
This console command lets you change the name tag of lamers.

``` lua
function iHateLamers ( thePlayer, commandName, playername )
    -- This is a command handler that activates on text "lamer" followed by the playername
    -- in the console. The playername argument was added as an extra function argument to store the
    -- name of the player whose text will be changed.
    if not playername then
        -- Prevents the command from running if the player did not specify a value for playername
        outputChatBox ( "You MUST define a player to change his name tag!", thePlayer )
    else
        local culprit = getPlayerFromName ( playername )
        -- This variable stores the result of trying to find the player associated with the playername
        -- that the user of the command specified
        if culprit then
            -- This checks to make sure a player nick was found. If it was not then the playername argument
            -- specified by the command user was not equivalent to the name of any players in the server
            setPlayerNametagText ( culprit, "IM_LAME" )
            -- finally, the nickname text is changed since the command arguments were checked and are valid
        else
            outputChatBox ( "Player does not exist!", thePlayer )
        end
    end
end
addCommandHandler ( "lamer", iHateLamers )
```

</section>
See Also
--------
