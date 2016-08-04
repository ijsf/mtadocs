This function is used to determine whether or not a player has a jetpack. Jetpacks can be given to players using the [givePlayerJetPack](/docs/givePlayerJetPack.md "wikilink") function and removed with the [removePlayerJetPack](/removePlayerJetPack.md "wikilink") function.

Syntax
------

``` lua
bool doesPlayerHaveJetPack ( player thePlayer )
```

### Required Arguments

-   **thePlayer**: The [player](/docs/player.md "wikilink") you are checking.

### Returns

Returns *true* if a player has a jetpack, *false* otherwise.

Example
-------

<section name="Server" class="server" show="true">
**Example 1:** This examples adds a “jetpack” console command, which gives or removes a jetpack from the player.

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

</section>
<section name="Server and client" class="both" show="true">
**Example 2:** This example provides a check to see if players have a jetpack when they enter a particular marker.

    function onWarpMarkerHit(thePlayer, matchingDimension)
       -- check whether the player has a jetpack and store it in the hasJetPack flag
       local hasJetPack = doesPlayerHaveJetPack(thePlayer)
       if (not hasJetPack) then
          -- warp the player to their destination
          setElementPosition(thePlayer, 1337, 1337, 50)
       else
          -- tell the player to remove their jetpack
          outputChatBox("You must remove your jetpack to use this marker!", thePlayer)
       end
    end

    -- create a marker and add the function above to its onMarkerHit event
    addEventHandler("onMarkerHit", createMarker(3180, 200, 27), onWarpMarkerHit)

</section>
See Also
--------
