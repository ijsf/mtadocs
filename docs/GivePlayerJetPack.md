This function is used to give a player a jetpack.

This function is not guaranteed to succeed. There are some cases where the jetpack cannot be given, for example:

-   If the player is in a vehicle
-   If the player is falling
-   Probably others too.

As such, you should either expect it to fail sometimes, or repeatedly try to give a jetpack every second or so until [doesPlayerHaveJetPack](/doesPlayerHaveJetPack.md "wikilink") returns true. Alternatively, you can force the player into a 'safe' position (e.g. standing on the ground) before giving the jetpack, or user a pickup to handle it.

Syntax
------

``` lua
bool givePlayerJetPack ( player thePlayer )
```

### Required Arguments

-   **thePlayer:** The [player](/player.md "wikilink") you want to give a jetpack to.

### Returns

Returns *true* if a jetpack was successfully given to the player, *false* if it could not be given.

Example
-------

This examples adds a “jetpack” console command, which gives or removes a jetpack from the player.

     [lua]
    -- Checks whether or not the player has a jetpack, and gives or removes it from the player
    function consoleJetPack ( thePlayer, commandName )
       if ( not doesPlayerHaveJetPack ( thePlayer ) ) then            -- if the player doesn't have a jetpack
          local status = givePlayerJetPack ( thePlayer )              -- give him one
          if ( not status ) then
             outputConsole ( "Failed to give jetpack.", thePlayer )   -- tell him if it failed
          end
       else
          local status = removePlayerJetPack ( thePlayer )            -- remove his jetpack
          if ( not status ) then
             outputConsole ( "Failed to remove jetpack.", thePlayer ) -- tell him if it failed
          end
       end
    end

    -- add the function above to handle the "jetpack" command
    addCommandHandler ( "jetpack", consoleJetPack )

See Also
--------
