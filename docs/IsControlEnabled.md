Checks whether a GTA control is enabled or disabled for a certain player.

Syntax
------

<section name="Server" class="server" show="true">
``` lua
bool isControlEnabled ( player thePlayer, string control )
```

### Required Arguments

-   **thePlayer:** The player you wish the control status of.
-   **control:** The control you wish to check. See [control names](/docs/control_names.md "wikilink") for a list of possible controls.

</section>
<section name="Client" class="client" show="true">
``` lua
bool isControlEnabled ( string control ) 
```

### Required Arguments

-   **control:** The control you wish to check. See [control names](/docs/control_names.md "wikilink") for a list of possible controls.

</section>
### Returns

Returns *true* if control is enabled, *false* otherwise.

Example
-------

<section name="Example 1" class="server" show="true">
This example uses a command handler to allow a player to toggle whether he can use vehicle weapons by disabling or enabling the primary and secondary vehicle fire keys. The command handler is trigged with 'toggleweapons'

``` lua
function changeWeaponControls ( player, commandName )
    --Check to see if the player can use primary/secondary vehicle fire controls
        primaryWeaponControl = isControlEnabled ( player, "vehicle_fire" )
        secondaryWeaponControl = isControlEnabled ( player, "vehicle_secondary_fire" )
    --Toggle the use of the primary vehicle fire control ability.
        if ( primaryWeaponControl == true ) then
             toggleControl ( player, "vehicle_fire", false )
             outputChatBox ( "Disabled your ability to use primary vehicle weapons." )
        else
             toggleControl ( player, "vehicle_fire", true )
             outputChatBox ( "Enabled your ability to use primary vehicle weapons." )
        end
        --Toggle the use of the secondar vehicle fire control ability.
        if ( secondaryWeaponControl == true ) then
             toggleControl ( player, "vehicle_secondary_fire", false )
             outputChatBox ( "Disabled your ability to use secondary vehicle weapons." )
        else
             toggleControl ( player, "vehicle_secondary_fire", true )
             outputChatBox ( "Enabled your ability to use secondary vehicle weapons." )
        end
end  
addCommandHandler ( "toggleweapons", changeWeaponControls )
```

</section>
See Also
--------
