Main Additions / Changes
------------------------

-   Anti-cheat updates
-   Optimized streamer to work better with complex maps
-   Smoothed fonts when scaling chat box
-   Added option to scale HUD elements correctly for widescreen
-   Added option to disable OS and graphic driver 'tweaks', as they can interfere with MTA
-   Better compatibility with NVidia Optimus laptops
-   Improved server performance
-   Updated our Audio Library to the latest version to improve some of our sound functions specifically beat detection and prevent crashes caused by calling getSoundMetaTags

### Client

------------------------------------------------------------------------

#### New Functions

-   [setVehiclePlateText](/docs/setvehicleplatetext.md "wikilink")
-   [dxSetAspectRatioAdjustmentEnabled](/docs/dxsetaspectratioadjustmentenabled.md "wikilink")

#### New Events

-   [onClientSoundStarted](/docs/onclientsoundstarted.md "wikilink")
-   [onClientSoundStopped](/docs/onclientsoundstopped.md "wikilink")

#### Changes / Bug Fixes

-   Optimized streamer to work better with complex maps
-   Smoothed fonts when scaling chat box
-   Added option to scale HUD elements correctly for widescreen
    -   This might cause your UI elements to scale incorrectly if they are based on the SA HUD positions this can be fixed with [dxSetAspectRatioAdjustmentEnabled](/docs/dxsetaspectratioadjustmentenabled.md "wikilink")
-   Added option to disable OS and graphic driver 'tweaks', as they can interfere with MTA
-   Better compatibility with NVidia Optimus laptops
-   Fixed GUI window remaining when you disconnect while starting local server
-   Fixed GUI labels sometimes blocking input
-   Fixed a crash on disconnect
-   Fixed [setVehicleLandingGearDown](/docs/setvehiclelandinggeardown.md "wikilink") not working sometimes
-   Added reassuring animation during periods of no input response
-   Fixed stability errors (random texture swapping/assertions) after alt+tab
-   Fixed some texture replace errors

### Server

------------------------------------------------------------------------

#### New Functions

-   [setVehiclePlateText](/docs/setvehicleplatetext.md "wikilink")
-   [getPlayerACInfo](/docs/getplayeracinfo.md "wikilink")

#### New Events

-   *None yet*

#### Changes / Bug Fixes

-   Fixed incorrect server side vehicle engine state when driver warped in
-   Fixed [onPlayerQuit](/docs/onplayerquit.md "wikilink") event not being triggered on shutdown
-   Fixed serverside [toggleAllControls](/docs/toggleallcontrols.md "wikilink")()

<!-- -->

-   Improved server performance
    -   by caching player weapon range
    -   by reducing the amount of redundant data sent to the network thread
-   Added CSimPedTaskPacket for better hit anim sync
-   Fixed an issue with weapon ammo getting out of sync
-   Sped up server scripts by optimizing ACL checks
-   Fixed some desyncs in unoccupied vehicle sync (engine, derailed, in-water state)
-   Fixed Get/SetMatrix rotation order for streamed out objects
-   Fixed Linux compile issues

<!-- -->

-   Fixed crash in ReApplyMoveAnims
-   Fixed [setElementPosition](/docs/setelementposition.md "wikilink") for players vehicle causing freeze for few seconds
-   Fixed [getPedTotalAmmo](/docs/getpedtotalammo.md "wikilink") sometimes returning 0 while player is aiming on Slot 8
-   Fixed [onPlayerDamage](/docs/onplayerdamage.md "wikilink") having wrong parameters if source on vehicle
-   Fixed [getVehicleSirens](/docs/getvehiclesirens.md "wikilink") on a sandking (495) crashing the server immediately
-   Fixed [onPlayerQuit](/docs/onplayerquit.md "wikilink") not calling on shutdown
-   Fixed [setJetpackWeaponEnabled](/docs/setjetpackweaponenabled.md "wikilink")() not working disabling jetpack weapons
-   Sped up server scripts slightly
-   Miscellaneous server optimizations

### Resources

-   \[**voice**\] Fixed voice icon not disappearing for other players after the speaking have been stopped (ccw)
-   \[**acpanel**\] Added acpanel
-   \[**admin**\] Fixed 'Set Team' button

### Editor

-   *None yet*

Extra information
-----------------

''More detailed information available on [Bug tracker Changelog](http://bugs.multitheftauto.com/changelog_page.php) and Google Code repositories:

:\* MTA:SA: from [r5357](http://code.google.com/p/mtasa-blue/source/list?num=25&start=5359) and [above](http://code.google.com/p/mtasa-blue/source/list)

:\* Resources: from [r930](http://code.google.com/p/mtasa-resources/source/list?num=25&start=930) and [above](http://code.google.com/p/mtasa-resources/source/list)

[Category:Changes in 1.3](/docs/category-changes_in_1.3.md "wikilink") [Category:Incomplete](/docs/category-incomplete.md "wikilink")
