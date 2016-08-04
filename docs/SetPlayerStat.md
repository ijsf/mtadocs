This function allows you to set the float value of a specific statistic for a [player](/player.md "wikilink"). **Visual stats (FAT and BODY\_MUSCLE) can only be used on the CJ skin.** A large number of the stats will have no effect.

Syntax
------

``` lua
bool setPlayerStat ( player thePlayer, int stat, float value )
```

### Required Arguments

-   **thePlayer**: the [player](/player.md "wikilink") whose statistic you want to modify.
-   **stat**: A whole number determining the stat ID.

-   **value**: A float number the stat will be set to. (0..999)

### Returns

Returns *true* if the statistic was changed succesfully. Returns *false* if an invalid player is specified, if the stat-id/value is out of acceptable range or if the FAT or BODY\_MUSCLE stats are used on non-CJ players.

Example
-------

This example allows a player to type the command 'beefcake' to change his player's BODY\_MUSCLE stat (\#23) to the maximum value of 999. This will result in him looking really muscular.

``` lua
function changeBodyStrength ( player, commandName )
    --Output whether the setPlayerStat was successful in changing the BODY_MUSCLE STAT     
    if ( setPlayerStat ( player, 23, 999 ) ) then
        outputChatBox ( "Your player looks really muscular" )
    else
        outputChatBox ( "Failed to make your player look muscular." )
    end
end
addCommandHandler ( "beefcake", changeBodyStrength )
```

See Also
--------
