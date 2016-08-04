This function sets the friendly fire value for the specified team.

Syntax
------

``` lua
bool setTeamFriendlyFire ( team theTeam , bool friendlyFire )
```

### Required Arguments

-   **theTeam:** The [team](/team.md "wikilink") that will have friendly fire set
-   **friendlyFire:** A boolean denoting whether friendly fire is on (*true*) or off (*false*).

### Returns

Returns *true* if the friendly fire value is set for the specified team, *false* if the friendly fire value can't be set for the specified team or if invalid arguments are specified.

Example
-------

This example checks if friendly fire is on for every team, and toggles it on if it isn't.

``` lua
-- get a table with all teams
local allTeams = getElementsByType ( "team" )
-- for every team,
for index, theTeam in ipairs(allTeams) do
    -- if friendly fire is off,
    if ( getTeamFriendlyFire ( theTeam ) == false ) then
        -- switch it on
        setTeamFriendlyFire ( theTeam, true )
    end
end
```

See Also
--------
