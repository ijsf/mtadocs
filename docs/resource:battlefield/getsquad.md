Purpose
-------

This command retrieves a [squad](/docs/Resource:Battlefield/squad.md "wikilink") element when given the name or [shortname](/Resource:Battlefield/shortname.md "wikilink") of a squad and the team.

Syntax
------

``` lua
squad getSquad ( [string squadName, string squadShortn], team squadTeam )
```

### Required Arguments

-   **squadTeam:** The [team](/docs/team.md "wikilink") element the squad will be attached to.

### Optional Arguments

-   **squadName:** The name of the squad.
-   **squadShortn:** The shortname of the squad.

### Returns

Returns the *squad element* if it was found, otherwise *false*.

Function Source
---------------

``` lua
nameTable = { "Alpha", "Bravo", "Charlie", "Delta", "Echo", "Foxtrot", "Golf", "Hotel" }
function getSquad ( name, team )
    local squads = getElementsByType ( "squad" )
    for k,v in ipairs ( squads ) do
        local sTeam = getElementData ( v, "team" )
        if team == sTeam then
            for j,l in ipairs ( nameTable ) do
                shortn = string.lower ( string.sub ( l, 1, 1 ) )
                if name == l or name == shortn then
                    return v
                else
                    return false
                end
            end
        else
            return false
        end
    end
end
```

|                                                                       |
|-----------------------------------------------------------------------|
| [Return to Battlefield Resource](/docs/Resource:Battlefield.md "wikilink") |
