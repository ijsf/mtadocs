This function is used to give a ped a jetpack, it won't work if the ped is in a vehicle.

As such, you should either expect it to fail sometimes, or repeatedly try to give a jetpack every second or so until [doesPedHaveJetPack](/docs/doespedhavejetpack.md "wikilink") returns true. Alternatively, you can force the ped into a 'safe' position (e.g. standing on the ground) before giving the jetpack, or use a [pickup](/docs/pickup.md "wikilink") to handle it.

Syntax
------

``` lua
bool givePedJetPack ( ped thePed )
```

### Required Arguments

-   **thePed:** The [ped](/docs/ped.md "wikilink") you want to give a jetpack to.

### Returns

Returns *true* if a jetpack was successfully given to the ped, *false* if it could not be given.

Example
-------

This examples adds a “jetpack” console command, which gives or removes a jetpack from the player.

    -- Checks whether or not the player has a jetpack, and gives or removes it from the player
    function consoleJetPack ( thePlayer, commandName )
       if not doesPedHaveJetPack ( thePlayer ) then                   -- if the player doesn't have a jetpack
          local status = givePedJetPack ( thePlayer )                 -- give him one
          if not status then
             outputConsole ( "Failed to give jetpack.", thePlayer )   -- tell him if it failed
          end
       else
          local status = removePedJetPack ( thePlayer )               -- remove his jetpack
          if ( not status ) then
             outputConsole ( "Failed to remove jetpack.", thePlayer ) -- tell him if it failed
          end
       end
    end

    -- add the function above to handle the "jetpack" command
    addCommandHandler ( "jetpack", consoleJetPack )

See Also
--------

[ru:givePedJetPack](/docs/ru:givepedjetpack.md "wikilink")
