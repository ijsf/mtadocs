Main Additions / Changes
------------------------

-   Huge code cleaups / optimizations
-   Improved performance browser
-   Improved mathematical precision for client and syncing
-   Bullet sync for sniper rifle

Scripting
---------

### Scripting: New functions

#### Client

-   Added [dxSetTextureEdge](/docs/dxsettextureedge.md "wikilink")
-   Added [guiEditGetCaretIndex](/docs/guieditgetcaretindex.md "wikilink")
-   Added [guiMemoGetCaretIndex](/docs/guimemogetcaretindex.md "wikilink")
-   Added [getCamera](/docs/getcamera.md "wikilink")
-   Added [setInteriorFurnitureEnabled](/docs/setinteriorfurnitureenabled.md "wikilink")
-   Added [getInteriorFurnitureEnabled](/docs/getinteriorfurnitureenabled.md "wikilink")

#### Server

-   None yet

#### Shared (*Client & Server side*)

-   Added [addDebugHook](/docs/adddebughook.md "wikilink")
-   Added [removeDebugHook](/docs/removedebughook.md "wikilink")
-   Added [base64Encode](/docs/base64encode.md "wikilink")
-   Added [base64Decode](/docs/base64decode.md "wikilink")
-   Added [teaEncode](/docs/teaencode.md "wikilink")
-   Added [teaDecode](/docs/teadecode.md "wikilink")
-   Added [pregFind](/docs/pregfind.md "wikilink")
-   Added [pregReplace](/docs/pregreplace.md "wikilink")
-   Added [pregMatch](/docs/pregmatch.md "wikilink")
-   Added [setElementCallPropagationEnabled](/docs/setelementcallpropagationenabled.md "wikilink")
-   Added [isElementCallPropagationEnabled](/docs/iselementcallpropagationenabled.md "wikilink")

### Scripting: New Events

#### Client

-   Added [onClientVehicleDamage](/docs/onclientvehicledamage.md "wikilink")

#### Server

-   None yet

### Scripting: Changes, Bugfixes and Additions

-   Added option to specify timeout length for [callRemote](/docs/callremote.md "wikilink") and [fetchRemote](/fetchRemote.md "wikilink")
-   Added error message parameter to [onPlayerScreenShot](/docs/onplayerscreenshot.md "wikilink") in case of failure
-   Added rotation parameter for [dxDrawText](/docs/dxdrawtext.md "wikilink")
-   Added flags (1 ignorecase; 2 multiline; 4 dotall; 8 extented) to preg functions
-   Added character option to preg option flags
-   Added easier way to set weapon flags
-   Added warning message for server scripts that might be causing a long freeze
-   Fixed some weapon flags
-   Fixed [isPedOnFire](/docs/ispedonfire.md "wikilink") not working correctly
-   Fixed [onPlayerVoiceStart](/docs/onplayervoicestart.md "wikilink") re-triggering when cancelled
-   Fixed double [dbPoll](/docs/dbpoll.md "wikilink") freeze
-   Fixed [setPedAimTarget](/docs/setpedaimtarget.md "wikilink") returning true for local player
-   Fixed [takePlayerScreenShot](/docs/takeplayerscreenshot.md "wikilink") sometimes returning a blank screen
-   Fixed event handler *sourceResource* global variable
-   Fixed [dxGetPixelsFormat](/docs/dxgetpixelsformat.md "wikilink") not recognising some jpeg files
-   Fixed [dxCreateFont](/docs/dxcreatefont.md "wikilink") not closing the file after creating font
-   Fixed [onPedWasted](/docs/onpedwasted.md "wikilink") / [onClientPedWasted](/onClientPedWasted.md "wikilink") always returning 63 (blown) as weapon
-   Fixed [setPedStat](/docs/setpedstat.md "wikilink") being sometimes not synced to client
-   Fixed [onClientSoundStopped](/docs/onclientsoundstopped.md "wikilink") sometimes being late
-   Fixed [attachElements](/docs/attachelements.md "wikilink") with the camera not removing the camera target
-   Fixed inability to bind num\_enter key
-   Fixed an inconsistence - Details: [r5852](https://code.google.com/p/mtasa-blue/source/detail?r=5852)
-   Fixed Backspace key not working in NoCurses mode
-   Fixed explosions created with [createExplosion](/docs/createexplosion.md "wikilink") passing through servers
-   Fixed [isElementInWater](/docs/iselementinwater.md "wikilink") returning false with peds
-   Fixed [guiScrollPaneSetHorizontalScrollPosition](/docs/guiscrollpanesethorizontalscrollposition.md "wikilink") and [guiScrollPaneSetVerticalScrollPosition](/guiScrollPaneSetVerticalScrollPosition.md "wikilink") not correctly using floating point numbers
-   Disabled [destroyElement](/docs/destroyelement.md "wikilink") and [setElementParent](/setElementParent.md "wikilink") for the camera element
-   Updated Lua to 5.1.5-2

Client
------

### Client: Additions

-   Added online help option for timed out error codes
-   Added more on-line help for in-game error messages
-   Added virus help messages to the loader
-   Added helpful messages for some crash types
-   Added upgrade message to uninstaller
-   Added disk space checks

### Client: Bugfixes & Changes

-   Fixed an issue when client runs with reduced mathematical precision compared to the server
-   Fixed problem with network floaters
-   Fixed escape key issue
-   Fixed ped Z position being sometimes out of sync
-   Fixed timeout problem with some gta\_sa.exe's
-   Fixed exploding vehicle causing issue with player death
-   Fixed some GUI crashes
-   Fixed client Lua crash
-   Fixed launch crash
-   Fixed crash caused by a custom model restoring conflict somewhere
-   Fixed a bug when throwing grenade could cause crash
-   Fixed [onClientElementStreamOut](/docs/onclientelementstreamout.md "wikilink") crash
-   Fixed graphics driver crash bug
-   Fixed another graphics driver crash bug
-   Fixed crash in loader
-   Fixed crash caused by element attachment problem somewhere
-   Fixed GUI skin change crash
-   Fixed depth buffer access (while antialiasing on) messing up screen output
-   Fixed getting wrong CJ clothes when spawning
-   Fixed problems with unicode install paths
-   Fixed problem of missing GTA language files
-   Fixed an issue when several vehicle colours result into black ones
-   Fixed damage proof boats still taking collision damage
-   Fixed vehicle color desync caused by setting paintjob
-   Fixed country rifle not inflicting damage without aiming
-   Fixed crouch roll glitch
-   Fixed a cursor alpha issue
-   Fixed ped attached objects sliding when ped walks on slopes
-   Fixed Intel clipping issues
-   Fixed [engineLoadTXD](/docs/engineloadtxd.md "wikilink") and [engineReplaceModel](/engineReplaceModel.md "wikilink") not properly closing invalid files
-   Fixed progress spinner not showing when server is using [latency reduction](/docs/mtaserver.conf#latency_reduction.md "wikilink")
-   Fixed network trouble message causing WSOD when server is using [latency reduction](/docs/mtaserver.conf#latency_reduction.md "wikilink")
-   Fixed progress spinner not showing when processing downloaded client files
-   Fixed Windows “Not responding” warning when client is busy
-   Fixed a bug when player could not enter any vehicle after trying to enter a vehicle in water
-   Fixed gta\_sa.exe not generating correctly
-   Fixed custom binds not saving properly
-   Fixed a startup freeze
-   Sped up [engineGetVisibleTextureNames](/docs/enginegetvisibletexturenames.md "wikilink")
-   Made glitches more compatible with [latency\_reduction](/docs/mtaserver.conf#latency_reduction.md "wikilink") mode
-   Improved bad install path detection on client launch
-   Improved client error messages
-   Tweaked client launcher trouble detection
-   Updated anti-virus detection
-   Unicode support for file paths

Server
------

### Server: Additions

-   Added 2 special detections - Details: [mtaserver.conf -&gt; enablesd](/docs/anti-cheat_guide#.3cenablesd.3e.3c.2fenablesd.3e.md "wikilink")
-   Added option to enable optimized vehicle parts state sync - Details: [r6107](https://code.google.com/p/mtasa-blue/source/detail?r=6107)
-   Added server option to log loadstring calls
-   Added option to compact internal databases
-   Added option to automatically update [minclientversion](/docs/mtaserver.conf#minclientversion.md "wikilink") - Details: [minclientversion\_auto\_update](/mtaserver.conf#minclientversion_auto_update.md "wikilink")
-   Added thread performance stats
-   Added server stats for RPC packets
-   Added server stats for usage of event and element data names
-   Updated performance stats to include open file count

### Server: Bugfixes & Changes

-   Fixed server stalls caused by open ports tester and master server announcer
-   Fixed several server crashes
-   Fixed [killPlayer](/docs/killplayer.md "wikilink") crashing server
-   Fixed a server exit crash
-   Fixed server crash during shutdown
-   Fixed server crash when calling [setControlState](/docs/setcontrolstate.md "wikilink") with a ped
-   Fixed server --maxplayers command line argument not working as advertised
-   Fixed includes failing when a resource changes
-   Fixed bug when player could not walk sideways while aiming with [latency\_reduction](/docs/mtaserver.conf#latency_reduction.md "wikilink") enabled
-   Fixed unnecessary syncing of attached marker positions
-   Fixed synced health and armor values so the fractional part is more consistent
-   Fixed vehicle wheel states not syncing properly
-   Tided server account handling
-   Tweaked server performance stats output
-   Improved mtasa:// protocol typo handler
-   Reduced memory usage for database query results
-   Removed sqlite external dependency

Resources
---------

-   \[**admin**\] Added some anticheat info
-   \[**admin**\] Fixed problems with certain player names
-   \[**race**\] Fixed rankingboard bug
-   \[**freeroam**\] Fixed vehicle command issue
-   \[**fastrope**\] Fixed being able to fall from super high and not get hurt
-   \[**parachute**\] Optimized resource - Details: [r966](https://code.google.com/p/mtasa-resources/source/detail?r=966), [r979](https://code.google.com/p/mtasa-resources/source/detail?r=979), [r980](https://code.google.com/p/mtasa-resources/source/detail?r=980), [r982](https://code.google.com/p/mtasa-resources/source/detail?r=982)
-   \[**parachute**\] Reduced server CPU and bandwidth usage
-   \[**parachute**\] Fixed some parachute stuff not working

Editor
------

-   Added support for hardcoded [fileCopy](/docs/filecopy.md "wikilink") function

Extra information
-----------------

''More detailed information available on [Bug tracker Changelog](https://bugs.multitheftauto.com/changelog_page.php) and Google Code repositories:

:\* MTA:SA: from [r5799](https://code.google.com/p/mtasa-blue/source/list?num=25&start=5804) to [r6156](https://code.google.com/p/mtasa-blue/source/list?num=25&start=6157)

:\* Resources: [from r955 to r991](https://code.google.com/p/mtasa-resources/source/list)

:\* [MTASA 1.3.5 released](http://forum.mtasa.com/viewtopic.php?f=31&t=71767)

[Category:Changes in 1.3](/docs/category:changes_in_1.3.md "wikilink") [Category:Incomplete](/Category:Incomplete.md "wikilink")

[pl:Changes in 1.3.5](/docs/pl:changes_in_1.3.5.md "wikilink") [pt-br:Novidades na versão 1.3.5](/pt-br:Novidades_na_versão_1.3.5.md "wikilink") [fi:Uutta versiossa 1.3.5](/fi:Uutta_versiossa_1.3.5.md "wikilink")
