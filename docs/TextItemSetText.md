Overwrites a previously created text item with the specified text.

Syntax
------

``` lua
void textItemSetText ( textitem theTextitem, string text )
```

### Required Arguments

-   **theTextitem:** An existing text item that was previously created with [textCreateTextItem](/textCreateTextItem.md "wikilink")
-   **text:** The new text for the text item

Example
-------

Here, it is being used to update a scoreboard:

``` lua
function updateScoreOnWasted ( ammo, killer, weapon )
    if ( killer ~= false) then                            -- Check to see if anything killed the player
        local killerTeam = getTeamName ( getPlayerTeam(killer) )
        if ( killerTeam == "grove" ) then             -- if a Grove player scored the kill
            groveteamscore = groveteamscore + 1   -- Grove gets 1 point
            textItemSetText ( scoregrove, tostring(groveteamscore) ) -- Update scoreboard.
        elseif ( killerTeam == "balla" ) then         -- if a Balla player scored the kill
            ballateamscore = ballateamscore + 1   -- Ballas get 1 point
            textItemSetText ( scoreballa, tostring(ballateamscore) ) -- Update scoreboard.
        end
    end
end
addEventHandler ( "onPlayerWasted", getRootElement(), updateScoreOnWasted )
```

See Also
--------
