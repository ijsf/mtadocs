<lowercasetitle/>

An useful function that gives you a table with the teams with less players. I've only put this here to replace a crappy function.

Syntax
------

``` lua
)
```

### Optional arguments

-   **teams**: a **regular indexed** table of teams. Example: {team, team, team, \[4\]=team}

### Return

Returns a table containing [teams](/docs/team.md "wikilink"). If it fails (invalid table provided) or if there are no teams; returns false.

Code
----

``` lua
function getTeamsWithFewestPlayers(t)
    if t and type(t)=="table" then -- Do checks for validity
        for i,v in ipairs(t) do
             if (not isElement(v)) or (type(v) ~= "team") then
                 -- Use stacktrace from debug to output a message to parent function
                 return false
             end
        end
    else t = getElementsByType("team") end
    local lowestScorers, lowestCount = {}, math.huge
    for i,v in ipairs(t) do
        local count = countPlayersInTeam(v)
        if count < lowestCount then
            lowestScorers = {v}
            lowestCount = count
        elseif count == lowestCount then
            table.insert(lowestScorers, v)
        end
    end
    return lowestScorers
end
```

Example
-------

<section name="Example" class="server" show="true">
This example adds a "/lowest" to tell the player which team has the lowest amount of players.

``` lua
-- Create a local function for the command "/lowest"
function lowestTeam(player)
    local teams = getTeamsWithFewestPlayers()
    local multiple = #teams > 1 -- is there more than one team?
    local teamListStr = ""
    for i,v in ipairs(teams) do
        local name = getTeamName(v)
        teamListStr = teamListStr .. " " .. name
        if (" "..teamListStr ~= name) and (i ~= #teams) then
            teamListStr = teamListStr .. " and"
        end
    end
    local str = string.format("The %s with the fewest players %s %s!", multiple and "teams" or "team", multiple and "are" or "is", teamListStr)
    outputChatBox(str, player)
end
addCommandHandler("lowest", lowestTeam)
```

</section>
Author: qaisjp

See Also
--------
