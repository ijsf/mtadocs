This function retrieves a squad element's team.

Syntax
------

``` lua
team getSquadTeam ( squad squadElement )
```

Required Argument
=================

-   **squadElement**: The squad you want to retrieve the team from.

Source Code
===========

``` lua
function getSquadTeam(squadElement)
    if(squadElement)then
        team = getElementData(squadElement,"team")
        return team
    else
        return false
    end
end
```

[<Resource:Battlefield>](/docs/resource:battlefield.md "wikilink")
