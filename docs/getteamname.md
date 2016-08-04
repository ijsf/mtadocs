This function gets the team name of a team object.

Syntax
------

``` lua
string getTeamName ( team theTeam )
```

### Required Arguments

-   **theTeam:** The team you want to retrieve the name of.

### Returns

Returns a string representing the team's name if the team object was valid, *false* otherwise.

Example
-------

This example gets the current team of a player, then prints its name to the chatbox.

``` lua
function whatTeamAmIOn (source)
    -- Get the player's team (source is the player who entered the command)
    local playerTeam = getPlayerTeam(source)
  
    if (playerTeam) then -- if he was on a team
        outputChatBox(getPlayerName(source).." is on team: "..getTeamName(playerTeam))
    else
        outputChatBox(getPlayerName(source).. " isn't on a team")
    end
end

-- Add console command to find your team when 'whatTeamAmIOn' is typed.
addCommandHandler("whatTeamAmIOn", whatTeamAmIOn)
```

See Also
--------
