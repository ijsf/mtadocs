This function will obtain the ID of a particular weapon from its name.

Syntax
------

``` lua
int getWeaponIDFromName ( string name )             
```

### Required Arguments

-   **name:** A [string](/docs/string.md "wikilink") containing the name of the weapon. Names can be: (Case is ignored)

### Returns

Returns an [int](/docs/int.md "wikilink") if the name matches that of a weapon, *false* otherwise.

Example
-------

<section name="Server" class="server" show="true">
This example will give the player the weapon they specify 20 ammo whenever they type “weapon *name*” into the console.

``` lua
-- Define our function that will handle this command
function consoleGiveWeapon ( playerSource, commandName, weapName )
    -- If a player triggered it (rather than the admin) then
    if ( playerSource ) then
        -- Get the weapon ID from the name
        local weapID = getWeaponIDFromName ( weapName )
        -- If it's a valid weapon
        if ( weapID ) then
            -- Give the weapon to the player
            giveWeapon ( playerSource, weapID, 20 )
            -- Output it in the chat box
            outputChatBox ( "You got a " .. weapName, playerSource )
        else outputChatBox ( "Invalid weapon name." )
        end
    end
end
-- Register the command handler and attach it to the 'consoleGiveWeapon' function
addCommandHandler ( "weapon", consoleGiveWeapon )
```

</section>
See Also
--------

[ru:getWeaponIDFromName](/docs/ru:getweaponidfromname.md "wikilink")
