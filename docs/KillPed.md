This function kills the specified ped.

Syntax
------

``` lua
 )
```

### Required Arguments

-   **thePed:** The [ped](/docs/ped.md "wikilink") to kill

### Optional Arguments

-   **theKiller:** The ped responsible for the kill
-   **weapon:** The ID of the weapon that should appear to have killed the ped (doesn't affect how they die)
-   **bodyPart:** The ID of the body part that should appear to have been hit by the weapon (doesn't affect how they die)

-   **stealth:** Boolean value, representing whether or not this a stealth kill

### Returns

Returns *true* if the ped was killed, *false* if the ped specified could not be killed or is invalid.

Example
-------

**Example 1:** This simple example adds a **kill** command to commit suicide.

``` lua
function commitSuicide ( sourcePlayer )
    -- kill the player and make him responsible for it
    killPed ( sourcePlayer, sourcePlayer )
end
-- attach our handler to the "kill" command
addCommandHandler ( "kill", commitSuicide )
```

**Example 2:** This example enables 1 hit kills if a player is shot in the head.

``` lua
function headshotKill ( attacker, attackerweapon, bodypart, loss )
    if bodypart == 9 then --if the bodypart is the head
        --kill the player, emulating the correct killer, weapon and bodypart.
        killPed ( source, attacker, attackerweapon, bodypart )
    end
end
addEventHandler ( "onPlayerDamage", getRootElement(), headshotKill )
```

Issues
------

See Also
--------

[ru:killPed](/docs/ru:killPed.md "wikilink")
