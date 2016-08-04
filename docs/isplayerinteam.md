This function checks if the specified [player](/docs/player.md "wikilink") is in the specified [team](/docs/team.md "wikilink").

Syntax
------

``` lua
bool isPlayerInTeam ( player thePlayer [, team/string theTeam = nil ] )
```

### Arguments

-   **thePlayer**: the [player](/docs/player.md "wikilink") you want to check if it's in the specified [team](/docs/team.md "wikilink").
-   **theTeam**: a [team](/docs/team.md "wikilink") element or name to check if the [player](/docs/player.md "wikilink") is in it. If not specified, this function will return *true* if the [player](/docs/player.md "wikilink") is in any [team](/docs/team.md "wikilink").

Code
----

<section name="Function source" class="both" show="true">
``` lua
function isPlayerInTeam(player, team)
    assert(isElement(player) and getElementType(player) == "player", "Bad argument 1 @ isPlayerInTeam [player expected, got " .. tostring(player) .. "]")
    assert((not team) or type(team) == "string" or (isElement(team) and getElementType(team) == "team"), "Bad argument 2 @ isPlayerInTeam [nil/string/team expected, got " .. tostring(team) .. "]")
    return getPlayerTeam(player) == (type(team) == "string" and getTeamFromName(team) or (type(team) == "userdata" and team or (getPlayerTeam(player) or true)))
end
```

</section>
Example
-------

<section name="Server" class="server" show="true">
This example adds a /onduty command which gives a cop uniform and nightstick to the player who types it, if he's on a team named “SAPD”.

``` lua
function duty(player)
    if isPlayerInTeam(player, "SAPD") then
        setElementModel(player, 280)
        setPedArmor(player, 100)
        takeAllWeapons(player)
        giveWeapon(player, 3, 1, true)
        outputChatBox("* Now " .. getPlayerName(player) .. " is on duty!", root, 0, 0, 200)
    end
end
addCommandHandler("onduty", duty)
```

</section>
See also
--------
