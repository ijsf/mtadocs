Main Additions / Changes
------------------------

### Client

------------------------------------------------------------------------

#### New Functions

-   Added [isPlayerHudComponentVisible](/docs/isPlayerHudComponentVisible.md "wikilink")
-   Added [setPlayerHudComponentVisible](/docs/setPlayerHudComponentVisible.md "wikilink") (alias of [showPlayerHudComponent](/showPlayerHudComponent.md "wikilink"))
-   Added [guiLabelGetColor](/docs/guiLabelGetColor.md "wikilink")
-   Added [isVoiceEnabled](/docs/isVoiceEnabled.md "wikilink")
-   Added [getPedOxygenLevel](/docs/getPedOxygenLevel.md "wikilink")
-   Added [setPedOxygenLevel](/docs/setPedOxygenLevel.md "wikilink")
-   Added [getVehicleComponentPosition](/docs/getVehicleComponentPosition.md "wikilink")
-   Added [getVehicleComponentRotation](/docs/getVehicleComponentRotation.md "wikilink")
-   Added [getVehicleComponentVisible](/docs/getVehicleComponentVisible.md "wikilink")
-   Added [resetVehicleComponentPosition](/docs/resetVehicleComponentPosition.md "wikilink")
-   Added [resetVehicleComponentRotation](/docs/resetVehicleComponentRotation.md "wikilink")
-   Added [setVehicleComponentPosition](/docs/setVehicleComponentPosition.md "wikilink")
-   Added [setVehicleComponentRotation](/docs/setVehicleComponentRotation.md "wikilink")
-   Added [setVehicleComponentVisible](/docs/setVehicleComponentVisible.md "wikilink")
-   Added [getVehicleComponents](/docs/getVehicleComponents.md "wikilink")
-   Added [engineGetModelLODDistance](/docs/engineGetModelLODDistance.md "wikilink")
-   Added [sha256](/docs/sha256.md "wikilink")
-   Added [setPedWalkingStyle](/docs/setPedWalkingStyle.md "wikilink")
-   Added [guiGridListSetColumnTitle](/docs/guiGridListSetColumnTitle.md "wikilink")
-   Added [guiGridListGetColumnTitle](/docs/guiGridListGetColumnTitle.md "wikilink")
-   Added [guiGridListGetVerticalScrollPosition](/docs/guiGridListGetVerticalScrollPosition.md "wikilink")
-   Added [guiGridListSetVerticalScrollPosition](/docs/guiGridListSetVerticalScrollPosition.md "wikilink")
-   Added [guiGridListGetHorizontalScrollPosition](/docs/guiGridListGetHorizontalScrollPosition.md "wikilink")
-   Added [guiGridListSetHorizontalScrollPosition](/docs/guiGridListSetHorizontalScrollPosition.md "wikilink")
-   Added [toggleObjectRespawn](/docs/toggleObjectRespawn.md "wikilink")
-   Added [breakObject](/docs/breakObject.md "wikilink")
-   Added [respawnObject](/docs/respawnObject.md "wikilink")
-   Added [isVehicleNitroRecharging](/docs/isVehicleNitroRecharging.md "wikilink")
-   Added [isVehicleNitroActivated](/docs/isVehicleNitroActivated.md "wikilink")
-   Added [getVehicleNitroCount](/docs/getVehicleNitroCount.md "wikilink")
-   Added [getVehicleNitroLevel](/docs/getVehicleNitroLevel.md "wikilink")
-   Added [setVehicleNitroActivated](/docs/setVehicleNitroActivated.md "wikilink")
-   Added [setVehicleNitroCount](/docs/setVehicleNitroCount.md "wikilink")
-   Added [setVehicleNitroLevel](/docs/setVehicleNitroLevel.md "wikilink")
-   Added [setAircraftMaxVelocity](/docs/setAircraftMaxVelocity.md "wikilink")
-   Added [getAircraftMaxVelocity](/docs/getAircraftMaxVelocity.md "wikilink")
-   Added [getMoonSize](/docs/getMoonSize.md "wikilink")
-   Added [setMoonSize](/docs/setMoonSize.md "wikilink")
-   Added [resetMoonSize](/docs/resetMoonSize.md "wikilink")
-   Added [guiStaticImageGetNativeSize](/docs/guiStaticImageGetNativeSize.md "wikilink")
-   Added [getObjectMass](/docs/getObjectMass.md "wikilink")
-   Added [setObjectMass](/docs/setObjectMass.md "wikilink")
-   Added [setCursorAlpha](/docs/setCursorAlpha.md "wikilink")
-   Added [getCursorAlpha](/docs/getCursorAlpha.md "wikilink")
-   Added [fetchRemote](/docs/fetchRemote.md "wikilink")
-   Added [bitAnd](/docs/bitAnd.md "wikilink")
-   Added [bitNot](/docs/bitNot.md "wikilink")
-   Added [bitOr](/docs/bitOr.md "wikilink")
-   Added [bitXor](/docs/bitXor.md "wikilink")
-   Added [bitTest](/docs/bitTest.md "wikilink")
-   Added [bitLRotate](/docs/bitLRotate.md "wikilink")
-   Added [bitRRotate](/docs/bitRRotate.md "wikilink")
-   Added [bitLShift](/docs/bitLShift.md "wikilink")
-   Added [bitRShift](/docs/bitRShift.md "wikilink")
-   Added [bitArShift](/docs/bitArShift.md "wikilink")
-   Added [bitExtract](/docs/bitExtract.md "wikilink")
-   Added [bitReplace](/docs/bitReplace.md "wikilink")
-   Added [setFPSLimit](/docs/setFPSLimit.md "wikilink")
-   Added [setSoundPan](/docs/setSoundPan.md "wikilink")
-   Added [getSoundPan](/docs/getSoundPan.md "wikilink")

#### New Events

-   Added [onClientVehicleNitroStateChange](/docs/onClientVehicleNitroStateChange.md "wikilink")
-   Added [onClientObjectBreak](/docs/onClientObjectBreak.md "wikilink")
-   Added [onClientObjectDamage](/docs/onClientObjectDamage.md "wikilink")
-   Added [onClientWeaponFire](/docs/onClientWeaponFire.md "wikilink")
-   Added [onClientVehicleDrown](/docs/onClientVehicleDrown.md "wikilink")
-   Added [onClientPlayerVoicePause](/docs/onClientPlayerVoicePause.md "wikilink")
-   Added [onClientPlayerVoiceResumed](/docs/onClientPlayerVoiceResumed.md "wikilink")

#### Changes / Bug Fixes

-   Fixed [setElementFrozen](/docs/setElementFrozen.md "wikilink") killing players from falls
-   Fixed textures disappearing and flickering at certain camera angles
-   Fixed high CPU usage when minimized and not connected
-   Integrated downgrader/patcher into the MTA installer
-   More fixes for engineless NRG-500
-   Fixed crashes on disconnect / reconnect
-   Fixed crashes when using [setFarClipDistance](/docs/setFarClipDistance.md "wikilink")
-   Fixed chinese characters in chat freezing the game
-   Fixed FarClipDistance reseting each respawn
-   Fixed [setFarClipDistance](/docs/setFarClipDistance.md "wikilink") messing with water drawing
-   Added an interior argument (optional) to [removeWorldModel](/docs/removeWorldModel.md "wikilink") and [restoreWorldModel](/restoreWorldModel.md "wikilink")
-   Fixed an issue when ped rotation while in air goes opposite direction by adding *conformPedAirRotation* argument to [setElementRotation](/docs/setElementRotation.md "wikilink")
-   Added work around to prevent server nitro adds cutting off recent client nitro adds
-   Fixed blank lines in the client console sometimes
-   Fixed launching issues with Steam
-   Added heat haze setting
-   Fixed crashes when getting combobox item text sometimes
-   Made [onClientChatMessage](/docs/onClientChatMessage.md "wikilink") cancelable
-   Fixed owning resource for client peds and water
-   Fixed custom collisions preventing normal collisions of other models from loading correctly
-   Fixed a bug when double-clicking on another server from server browser list while connecting to a server makes the game exit to desktop
-   Fixed crash when destroying the source of [onClientColShapeHit](/docs/onClientColShapeHit.md "wikilink") event
-   Fixed an error with [setVehicleSirens](/docs/setVehicleSirens.md "wikilink")
-   Conformed client console log date format to ISO 8601
-   Fixed custom dx-fonts not working on Windows 8
-   Prevented loading splash disappearing too early
-   Fixed readable depth buffer not working with anti-aliasing
-   Improved performance of readable depth buffer/AA fix - Details: [Depth buffer](/docs/DepthBuffer.md "wikilink")
-   Added more settings to [dxGetStatus](/docs/dxGetStatus.md "wikilink")
-   Reduced chance of message boxes being obscured by other windows
-   Fixed not working crouching with vehicle extrapolation
-   Fixed startup issue with an exe version that someone gave support desk
-   Fixed stuck voice problem
-   Fixed [onClientPlayerVoiceStop](/docs/onClientPlayerVoiceStop.md "wikilink") not working properly
-   Fixed occasional invalid return value from [getEasingValue](/docs/getEasingValue.md "wikilink")
-   Added color coded argument to [dxGetTextWidth](/docs/dxGetTextWidth.md "wikilink")
-   Main menu items 'Map Editor'/'Host Game' now will ask if player want to disconnect from current server
-   Added proper axis support on controllers
-   Fixed *hitElement* parameter working incorrectly with shotgun in [onClientPlayerWeaponFire](/docs/onClientPlayerWeaponFire.md "wikilink")
-   Fixed and re-enabled [setPedWalkingStyle](/docs/setPedWalkingStyle.md "wikilink")
-   Added ped vertex [shader](/docs/shader.md "wikilink") support
-   Fixed [engineGetModelTextureNames](/docs/engineGetModelTextureNames.md "wikilink") for CJ model
-   Small memory optimization for the server browser
-   Fixed [guiGetEnabled](/docs/guiGetEnabled.md "wikilink") and [guiGetVisible](/guiGetVisible.md "wikilink") for tabs
-   Fixed binds that were attached directly to controls getting reset when loading default binds in settings
-   Fixed [getVehicleType](/docs/getVehicleType.md "wikilink") with trailers returning empty string client-side
-   Fixed chat messages not updating while a map download is in progress
-   Fixed server browser disabled tab option
-   Added cached info for server browser favourites
-   Fixed startup issues
-   Make [setObjectScale](/docs/setObjectScale.md "wikilink") accept 1 scale value for each axis
-   Fixed not properly working client's console logging
-   Fixed readable depth buffer not working on some graphic cards
-   Fixed object scale crash
-   Refixed scaled objects not being rendered when the unscaled bounding box goes off-screen
-   Made it able to set velocity on (dynamic) objects
-   Fixed radararea not functioning when using negative numbers for dimensions
-   Improved frozen process detection
-   Fixed client quit issue
-   Fixed quit crash when connection history drop-down is visible
-   Fixed input settings inconsistencies
-   Added vertical aim sensitivity setting
-   Fixed [guiGetSelectedTab](/docs/guiGetSelectedTab.md "wikilink") crash after removing a tab
-   Added target position as alternative to [setCameraTarget](/docs/setCameraTarget.md "wikilink")
-   Added process priority setting
-   Improved installer
-   Fixed PNG files with alpha channel sometimes being all black
-   Added car number plates, road sign text, CJ body parts and unnamed textures to [engineApplyShaderToWorldTexture](/docs/engineApplyShaderToWorldTexture.md "wikilink")
-   Added some BASS API functions to voice - Details: [Google Code](http://code.google.com/p/mtasa-blue/source/detail?r=5247)
-   Added clothing component textures to [engineImportTXD](/docs/engineImportTXD.md "wikilink")
-   Reduced stutter/lags on big maps
-   Fixed [depth buffer](/docs/depthBuffer.md "wikilink") [shaders](/Shader.md "wikilink") not working right with mirrors
-   Fixed client crash after login and spawn
-   Added ability to turn off sounds when MTA:SA is minimized
-   Sped up deletion of certain client element types
-   Enhanced quality on usage of non-power of two image sizes for [dxDrawImage](/docs/dxDrawImage.md "wikilink")
-   Added bitwise operator functions
-   Added a record for when a player connects to a server
-   Added *alphaTransparency* argument to [engineReplaceModel](/docs/engineReplaceModel.md "wikilink")
-   Fixed a server browser crash
-   Added 'showframegraph' command for displaying frame timings
-   Added 'sinfo' command to output server info
-   Fixed freeze on connect
-   Fixed [isObjectBreakable](/docs/isObjectBreakable.md "wikilink") returning wrong values sometimes
-   Added the model id as an alternative parameter to [isObjectBreakable](/docs/isObjectBreakable.md "wikilink")
-   Fixed vehicles losing velocity on race respawn

### Server

------------------------------------------------------------------------

#### New Functions

-   Added [setPlayerHudComponentVisible](/docs/setPlayerHudComponentVisible.md "wikilink")
-   Added [sha256](/docs/sha256.md "wikilink")
-   Added [getMoonSize](/docs/getMoonSize.md "wikilink")
-   Added [setMoonSize](/docs/setMoonSize.md "wikilink")
-   Added [resetMoonSize](/docs/resetMoonSize.md "wikilink")
-   Added [bitAnd](/docs/bitAnd.md "wikilink")
-   Added [bitNot](/docs/bitNot.md "wikilink")
-   Added [bitOr](/docs/bitOr.md "wikilink")
-   Added [bitXor](/docs/bitXor.md "wikilink")
-   Added [bitTest](/docs/bitTest.md "wikilink")
-   Added [bitLRotate](/docs/bitLRotate.md "wikilink")
-   Added [bitRRotate](/docs/bitRRotate.md "wikilink")
-   Added [bitLShift](/docs/bitLShift.md "wikilink")
-   Added [bitRShift](/docs/bitRShift.md "wikilink")
-   Added [bitArShift](/docs/bitArShift.md "wikilink")
-   Added [bitExtract](/docs/bitExtract.md "wikilink")
-   Added [bitReplace](/docs/bitReplace.md "wikilink")

#### New Events

-   *None yet*

#### Changes / Bug Fixes

-   Added crash handler for Linux (It outputs log files in dumps/)
-   Added account name to [whowas](/docs/Server_Commands#whowas.md "wikilink") command
-   Added an interior argument (optional) to [removeWorldModel](/docs/removeWorldModel.md "wikilink") and [restoreWorldModel](/restoreWorldModel.md "wikilink")
-   Fixed an issue when ped rotation while in air goes opposite direction by adding *conformPedAirRotation* argument to [setElementRotation](/docs/setElementRotation.md "wikilink")
-   Added auto generation of correct [min\_mta\_version](/docs/meta.xml#<min_mta_version_/>.md "wikilink") to 'upgrade' command
-   Changed ['upgrade'](/docs/Server_Commands#upgrade.md "wikilink") and ['check'](/Server_Commands#check.md "wikilink") commands to also work on single resources
-   Fixed file download not working on some servers
-   Added network filter option
-   Fixed server crash when deleting element in [onResourceStop](/docs/onResourceStop.md "wikilink")
-   Same serial now can't be banned more than once
-   Fixed [fixdb](/docs/fixdb.md "wikilink") problems
-   Fixed an error with [setVehicleSirens](/docs/setVehicleSirens.md "wikilink")
-   Fixed [getVehicleSirensOn](/docs/getVehicleSirensOn.md "wikilink") returning a nil value
-   Fixed double collisions when changing marker type
-   Added 3 new special detections - Details: [mtaserver.conf -&gt; enablesd](/docs/Anti-cheat_guide#.3Cenablesd.3E.3C.2Fenablesd.3E.md "wikilink")
-   Fixed 'suppress' option in [dbConnect](/docs/dbConnect.md "wikilink")
-   Added access to a couple of [dbConnect](/docs/dbConnect.md "wikilink") logging settings
-   Tweaked ASE port usage
-   Added cpu core stats for Linux server
-   Changed account passwords to use salted sha256
-   Fixed issue when element is destroyed client sided when created and parent set in different resource than the parent
-   Sped up accounts upgrade
-   Fixed target range, accuracy and weapon range
-   Fixed [setRuleValue](/docs/setRuleValue.md "wikilink") crash
-   Fixed the client-side scripts “protected” attribute not working on Linux servers
-   Fixed occasional crash when empty filename used for some functions
-   Fixed a problem where [onResourceStart](/docs/onResourceStart.md "wikilink") is not triggered for the root element when using [startResource](/startResource.md "wikilink") from inside a (root attached) event handler
-   Added resource name and bandwidth usage to function performance stats
-   Added [latency\_reduction](/docs/mtaserver.conf#latency_reduction.md "wikilink") option to [mtaserver.conf](/mtaserver.conf.md "wikilink")
-   Fixed and re-enabled [setPedWalkingStyle](/docs/setPedWalkingStyle.md "wikilink")
-   Fixed [setElementDimension](/docs/setElementDimension.md "wikilink") not working on children
-   Added “shared” script type to [meta.xml](/docs/meta.xml.md "wikilink")
-   Decreased CPU usage by speeding up event lookups
-   Fixed *visibleTo* argument not checking for errors in [outputChatBox](/docs/outputChatBox.md "wikilink")
-   Tidied ASE functionality
-   Fixed Windows server HTTP download compression (for [fetchRemote](/docs/fetchRemote.md "wikilink"))
-   Fixed client using HTTP download compression
-   Fixed vehicle extrapolation camera smoothness when viewing remote vehicles
-   Updated server performance stats
-   Fixed Linux core number in stats
-   Slightly sped up server startup
-   Fixed trailers desync
-   Fixed train desync
-   Synchronized ped traffic light
-   Fixed markers created by .map-files having wrong colshapes
-   Added process memory to performance stats
-   Fixed server 'per player entity' crash
-   Fixed [warpPedIntoVehicle](/docs/warpPedIntoVehicle.md "wikilink") after [cancelEvent](/cancelEvent.md "wikilink") of [onVehicleStartEnter](/onVehicleStartEnter.md "wikilink") causing network trouble
-   Added 'hitanim' glitch to [setGlitchEnabled](/docs/setGlitchEnabled.md "wikilink") (shot hit animation)
-   Added server setting to change syncer distances
-   Added server multiple IP support
-   Fixed [xmlFindChild](/docs/xmlFindChild.md "wikilink") after [xmlSetNodeValue](/xmlSetNodeValue.md "wikilink") causing a crash
-   Fixed [getPedTotalAmmo](/docs/getPedTotalAmmo.md "wikilink") not returning the correct values

### Resources

-   \[**fallout**\] Fixed freecam locks
-   \[**scoreboard**\] Added support for data to be drawn as image - Details: [Google Code](http://code.google.com/p/mtasa-resources/source/detail?r=882)
-   \[**voice**\] Added 'mutevoice' and 'unmutevoice' commands for players to mute other players permanently - Details: [Google Code](http://code.google.com/p/mtasa-resources/source/detail?r=882)
-   \[**admin**\] Added custom ban duration when banning player via GUI
-   \[**admin**\] Added ability to delete resource in 'Resources' tab (new [ACL](http://wiki.multitheftauto.com/wiki/ACL) right 'command.delete')
-   \[**admin**\] Added ability to stop all resources in 'Resources' tab
-   \[**admin**\] More informations about resources now showing in 'Resources' tab
-   \[**admin**\] Added ability to shutdown the server in 'Server' tab
-   \[**admin**\] Changing vehicle's color now supports new RGB system, color is picked using color picker
-   \[**admin**\] Vehicle's lights color can now be changed
-   \[**admin**\] Server FPS Limit can now be changed in 'Server' tab
-   \[**webadmin**\] Added 'Players' tab where you can kick/ban players on server
-   \[**ipb**\] Added Ingame Performance Browser - Details: [Google Code](http://code.google.com/p/mtasa-resources/source/detail?r=896)
-   \[**votemanager**\] Fixed an error when votemanager can't start votekick, votekill or voteban, if the player, who we want to vote, name contains 1 character
-   \[**race**\] Added editor visualization of checkpoint connections
-   \[**admin**\] Added ability to view players' screen

### Editor

-   Fixed 'Locked Time' option resetting
-   Reduced the size of map files
-   Fixed some settings not resetting when you start a new map after working in another
-   Fixed weapon model changes to 1337 after saving/loading some times
-   Fixed problem with invalid editor\_dump
-   Fixed not loading objects properly when a vehicle position attribute isn't saved
-   Added ability to remove world objects in editor
-   Added ability to include low LOD models for some objects
-   Map Editor won't remove script lines in meta.xml

Extra information
-----------------

''More detailed information available on [Bug tracker Changelog](http://bugs.multitheftauto.com/changelog_page.php) and Google Code repositories:

:\* MTA:SA: from [r4600](http://code.google.com/p/mtasa-blue/source/list?num=25&start=4605) and [above](http://code.google.com/p/mtasa-blue/source/list)

:\* Resources: from [r875](http://code.google.com/p/mtasa-resources/source/list?num=25&start=883) and [above](http://code.google.com/p/mtasa-resources/source/list)

[Category:Changes in 1.3](/docs/Category:Changes_in_1.3.md "wikilink")
