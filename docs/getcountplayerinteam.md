**Note:** Use [countPlayersInTeam](/docs/countPlayersInTeam.md "wikilink") instead

This function get count [player](/docs/player.md "wikilink") in [team](/team.md "wikilink").

Syntax
------

``` lua
int getCountPlayerInTeam ( team )
```

### Arguments

-   **team**: a [team](/docs/team.md "wikilink") to get count players in this team.

### Returns

Returns *int* of count players.

Code
----

<section name="Function source" class="both" show="true">
``` lua
function getCountPlayerInTeam ( team )
    assert ( isElement ( team ) and getElementType ( team ) == "team", "Bad argument @ getCountPlayerInTeam [ team expected, got " .. type ( team ) .. " ]" )
    local countPlayer = 0
    for _,v in ipairs ( getElementsByType ( "player" ) ) do
        if ( getPlayerTeam ( v ) == team ) then
            countPlayer = countPlayer + 1
        end
    end
    return countPlayer
end
```

</section>
By AboShanab.

See also
--------
