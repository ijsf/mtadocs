This function finds a team object by the team's name.

Syntax
------

``` lua
team getTeamFromName ( string teamName )
```

### Required Arguments

-   **teamName:** A string determining the name of the team you wish to find.

### Returns

Returns the team object if it was found, *false* otherwise.

Example
-------

This example creates a team, and sets the player's team to it's partial name:

``` lua
-- Creates a red team
createTeam("Red", 255, 0, 0)

function joinRedTeam (source)
    local redteam = getTeamFromName("Red")
    if (redteam) then -- If the team was successfully created
        -- Sets the player's team by getting the partial name of the red team.
        setPlayerTeam(client, readteam)
        outputChatBox("You are now in the 'Red' team", source)
    else
        outputChatBox("Sorry, we can't set your team. An error occurred!", source)
    end
end

--Add console command to join the team when 'joinTeam' is typed.
addCommandHandler("jointeam", joinRedTeam)
```

See Also
--------
