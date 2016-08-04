This function changes the size of an existing [radar area](/radararea.md "wikilink").

Syntax
------

``` lua
bool setRadarAreaSize ( radararea theRadararea, float x, float y )
```

### Required Arguments

-   **theRadararea:** the [radararea](/radararea.md "wikilink") element whose size is to be changed.
-   **x:** the x length of the radar area.
-   **y:** the y length of the radar area.

### Returns

Returns *true* if the size was set successfully, *false* if invalid arguments are passed.

Example
-------

**Example 1:** This example decreases the size of a team's radar area whenever a player from that team dies:

``` lua
-- assume that team elements exist and that each player belongs to one of them
-- assume that radararea elements exist and that each is a child of one of the teams
function playerWasted ( killer, killerweapon, bodypart )
    local victimteam = getPlayerTeam ( source )                 -- get the team of the victim
    local killerteam = getPlayerTeam ( killer )                 -- get the team of the killer
    if ( killer and killerteam ~= victimteam ) then             -- if there is a killer and he is from an opposing team
        local victimarea = getElementChild ( victimteam, 0 )    -- get the radararea belonging to the victim's team
        local x, y = getRadarAreaSize ( victimarea )            -- get the size of the radar area
        x = x - 5
        y = y - 5
        setRadarAreaSize ( victimarea, x, y )                   -- set a new (smaller) size for the victim's radar area
    end
end
addEventHandler ( "onPlayerWasted", root, playerWasted )
```

**Example 2:** This example creates a radar area and resets its size right away:

``` lua
aRadarArea = createRadarArea ( 1024, 1024, 30, 140, 255, 255, 0, 85 )
flag = setRadarAreaSize ( aRadarArea, 50, 90 )
if ( flag ) then
    outputChatBox ( "Radar area size set successfully!" )
else
    outputChatBox ( "Failed to set radar area size." )
end
```

See Also
--------
