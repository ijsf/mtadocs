This function allows you to set the value of a specific statistic for a [ped](/ped.md "wikilink"). **Visual stats (FAT and BODY\_MUSCLE) can only be used on the CJ skin**, they have no effect on other skins.

Syntax
------

``` lua
bool setPedStat ( ped thePed, int stat, float value )
```

### Required Arguments

-   **thePed**: the [ped](/ped.md "wikilink") whose statistic you want to modify.
-   **stat**: the stat ID.

-   **value**: the new value of the stat. It must be between 0 and 1000.

### Returns

Returns *true* if the statistic was changed succesfully. Returns *false* if an invalid player is specified, if the stat-id/value is out of acceptable range or if the FAT or BODY\_MUSCLE stats are used on non-CJ players.

Examples
--------

This example allows a player to type the command 'beefcake' to change his player's BODY\_MUSCLE stat (\#23) to the maximum value of 1000. This will result in him looking really muscular.

``` lua
function changeBodyStrength(thePlayer, commandName)
    -- Output whether the setPlayerStat was successful in changing the BODY_MUSCLE STAT     
    if setPedStat(thePlayer, 23, 1000) then
        outputChatBox("Your player looks really muscular")
    else
        outputChatBox("Failed to make your player look muscular.")
    end
end
addCommandHandler("beefcake", changeBodyStrength)
```

This example adds a */upgradeskills* command to give the player who types it the maximum skill with every weapon and maximum health.

``` lua
--[[

Skills to upgrade:

24 = Max Player Health
69 = Weapon Type Pistol Skill
70 = Weapon Type Pistol Silenced Skill
71 = Weapon Type Desert Eagle Skill
72 = Weapon Type Shotgun Skill
73 = Weapon Type Sawn off Shotgun Skill
74 = Weapon Type Spas 12 Shotgun Skill
76 = Weapon Type MP5 Skill
77 = Weapon Type AK47 Skill
78 = Weapon Type M4 Skill
79 = Weapon Type Sniper Rifle Skill

--]]

addCommandHandler("upgradeskills", function(thePlayer)
   -- Set every stat to 1000 (the maximum value)
   for _, stat in ipairs({ 24, 69, 70, 71, 72, 73, 74, 76, 77, 78, 79 }) do
      setPedStat(thePlayer, stat, 1000)
   end
   -- Set player health to the maximum, as changing the stat keeps the current one
   setElementHealth(thePlayer, 200)
   -- Tell the player what we did
   outputChatBox("Weapon skills and health upgraded to maximum!", thePlayer, 0, 255, 0)
end)
```

See Also
--------

[ru:setPedStat](/ru:setPedStat.md "wikilink")
