Purpose
-------

Creates a squad element. [Click here to read more about squads.](/docs/Resource:battlefield/squad.md "wikilink")

Syntax
------

``` lua
squad createSquad ( team squadTeam, string shortName )
```

### Required Arguments

-   **squadTeam:** The [team](/docs/team.md "wikilink") element the squad will be attached to.
-   **shortName:** The [shortname](/docs/Resource:battlefield/shortname.md "wikilink") for the squad.

### Returns

Returns the *squad element* if it was created, otherwise *false*.

Function Source
---------------

``` lua
function createSquad ( team, shortn )
    squad = createElement ( "squad", team, shortn )
    if squad then
        return squad
    else
        return false
    end
end
```

|                                                                       |
|-----------------------------------------------------------------------|
| [Return to Battlefield Resource](/docs/Resource:Battlefield.md "wikilink") |
