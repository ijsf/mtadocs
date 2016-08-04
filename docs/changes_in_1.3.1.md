Main Additions / Changes
------------------------

-   Added Custom Vehicle Sirens
-   Fixed map files are downloading very slow issue
-   Fixed timeouts on map change
-   Fixed various issues, crashes and freezes
-   Updated max players to 4096
-   Added BASS Effects
-   Added Analog Controls States
-   Added bullet sync
-   Fixed several custom model replacing issues
-   Windows 8 support (both 32-bits and 64-bits)
-   Added ability to create pedless weapons via weapon creation
-   Improved Map Editor stability and added new features
-   Installers for regular builds and nightlies are now digitally signed

Client
------

### New Functions

-   Added [setObjectBreakable](/docs/setobjectbreakable.md "wikilink")
-   Added [isObjectBreakable](/docs/isobjectbreakable.md "wikilink")
-   Added [dxSetBlendMode](/docs/dxsetblendmode.md "wikilink")
-   Added [dxGetBlendMode](/docs/dxgetblendmode.md "wikilink")
-   Added [dxDrawMaterialLine3D](/docs/dxdrawmaterialline3d.md "wikilink")
-   Added [dxDrawMaterialSectionLine3D](/docs/dxdrawmaterialsectionline3d.md "wikilink")
-   Added [getLatentEventHandles](/docs/getlatenteventhandles.md "wikilink")
-   Added [getLatentEventStatus](/docs/getlatenteventstatus.md "wikilink")
-   Added [cancelLatentEvent](/docs/cancellatentevent.md "wikilink")
-   Added [triggerLatentServerEvent](/docs/triggerlatentserverevent.md "wikilink")
-   Added [getVehicleSirenParams](/docs/getvehiclesirenparams.md "wikilink")
-   Added [getVehicleSirens](/docs/getvehiclesirens.md "wikilink")
-   Added [setVehicleSirens](/docs/setvehiclesirens.md "wikilink")
-   Added [getSoundProperties](/docs/getsoundproperties.md "wikilink")
-   Added [setSoundProperties](/docs/setsoundproperties.md "wikilink")
-   Added [getSoundFFTData](/docs/getsoundfftdata.md "wikilink")
-   Added [setSoundPanningEnabled](/docs/setsoundpanningenabled.md "wikilink")
-   Added [isSoundPanningEnabled](/docs/issoundpanningenabled.md "wikilink")
-   Added [setWorldSoundEnabled](/docs/setworldsoundenabled.md "wikilink")
-   Added [isWorldSoundEnabled](/docs/isworldsoundenabled.md "wikilink")
-   Added [resetWorldSounds](/docs/resetworldsounds.md "wikilink")
-   Added [getSoundBPM](/docs/getsoundbpm.md "wikilink")
-   Added [getSoundLevelData](/docs/getsoundleveldata.md "wikilink")
-   Added [getSoundWaveData](/docs/getsoundwavedata.md "wikilink")
-   Added [setPedAnalogControlState](/docs/setpedanalogcontrolstate.md "wikilink")
-   Added [getPedAnalogControlState](/docs/getpedanalogcontrolstate.md "wikilink")
-   Added [setAnalogControlState](/docs/setanalogcontrolstate.md "wikilink")
-   Added [getAnalogControlState](/docs/getanalogcontrolstate.md "wikilink")
-   Added [setPedTargetingMarkerEnabled](/docs/setpedtargetingmarkerenabled.md "wikilink")
-   Added [isPedTargetingMarkerEnabled](/docs/ispedtargetingmarkerenabled.md "wikilink")
-   Added [setElementMatrix](/docs/setelementmatrix.md "wikilink")
-   Added [warpPedIntoVehicle](/docs/warppedintovehicle.md "wikilink")
-   Added [removePedFromVehicle](/docs/removepedfromvehicle.md "wikilink")
-   Added [setProjectileCounter](/docs/setprojectilecounter.md "wikilink")
-   Added [createWeapon](/docs/createweapon.md "wikilink")
-   Added [fireWeapon](/docs/fireweapon.md "wikilink")
-   Added [setWeaponProperty](/docs/setweaponproperty.md "wikilink")
-   Added [setWeaponState](/docs/setweaponstate.md "wikilink")
-   Added [setWeaponTarget](/docs/setweapontarget.md "wikilink")
-   Added [getWeaponOwner](/docs/getweaponowner.md "wikilink")
-   Added [setWeaponOwner](/docs/setweaponowner.md "wikilink")
-   Added [setWeaponFlags](/docs/setweaponflags.md "wikilink")
-   Added [getWeaponFlags](/docs/getweaponflags.md "wikilink")
-   Added [setWeaponFiringRate](/docs/setweaponfiringrate.md "wikilink")
-   Added [getWeaponFiringRate](/docs/getweaponfiringrate.md "wikilink")
-   Added [resetWeaponFiringRate](/docs/resetweaponfiringrate.md "wikilink")
-   Added [getWeaponClipAmmo](/docs/getweaponclipammo.md "wikilink")
-   Added [setWeaponClipAmmo](/docs/setweaponclipammo.md "wikilink")
-   Added [getWeaponAmmo](/docs/getweaponammo.md "wikilink")
-   Added [setWeaponAmmo](/docs/setweaponammo.md "wikilink")
-   Added [getProjectileCounter](/docs/getprojectilecounter.md "wikilink")
-   Added [setWaterDrawnLast](/docs/setwaterdrawnlast.md "wikilink")
-   Added [isWaterDrawnLast](/docs/iswaterdrawnlast.md "wikilink")
-   Added [guiLabelGetColor](/docs/guilabelgetcolor.md "wikilink")

### New Events

-   Added [onClientPedHeliKilled](/docs/onclientpedhelikilled.md "wikilink")
-   Added [onClientPlayerHeliKilled](/docs/onclientplayerhelikilled.md "wikilink")
-   Added [onClientPlayerHitByWaterCannon](/docs/onclientplayerhitbywatercannon.md "wikilink")
-   Added [onClientPedHitByWaterCannon](/docs/onclientpedhitbywatercannon.md "wikilink")
-   Added [onClientPlayerPickupHit](/docs/onclientplayerpickuphit.md "wikilink")
-   Added [onClientPlayerPickupLeave](/docs/onclientplayerpickupleave.md "wikilink")
-   Added [onClientSoundBeat](/docs/onclientsoundbeat.md "wikilink")
-   Added [onClientWeaponFire](/docs/onclientweaponfire.md "wikilink")

### Changes / Bug Fixes

-   Fixed 'not being able to enter vehicles' bug
-   Added order priority to [addEventHandler](/docs/addeventhandler.md "wikilink")
-   Fixed 'engineless' NRG-500 Variant
-   Added option to skip Dual Monitor Resolution Select
-   Made [playSound3D](/docs/playsound3d.md "wikilink") use the camera position instead of the player position when determining the distance
-   Added color coding and sub-pixel positioning options to [dxDrawText](/docs/dxdrawtext.md "wikilink")
-   Added ability to create and modify cubemaps and volume textures - Details: [dxCreateTexture](/docs/dxcreatetexture.md "wikilink")
-   Added model cache system to reduce loading delays
-   Added CJ clothes cache to help reduce game freezes
-   Sped up event handling system for server and client
-   Added element option to [engineApplyShaderToWorldTexture](/docs/engineapplyshadertoworldtexture.md "wikilink")
-   Added optional bool to [getElementMatrix](/docs/getelementmatrix.md "wikilink") ( element, bool )
-   Added unrar for smoother update procedure
-   Fixed custom model replacement errors sometimes with weapons & weapon pickups.
-   Fixed vehicle upgrade custom models not showing immediately
-   Fixed accuracy of hit point in [onClientPlayerWeaponFire](/docs/onclientplayerweaponfire.md "wikilink") and added shot origin parameter
-   Fixed [setPedAimTarget](/docs/setpedaimtarget.md "wikilink") direction being all wrong
-   Fixed issue when peds' bullets origin from wrong position
-   Fixed custom models not rendering correctly sometimes parameter
-   Fixed custom model LOD distance is not reseting after quiting
-   Added size limit for clientscript.log file
-   Added ability to shoot with any weapon with jetpack
-   Made timers less crashy
-   Fixed some animation crashes
-   Fixed [getPedMoveState](/docs/getpedmovestate.md "wikilink") returns false when moving in crouch state
-   Fixed a bug when a resource that replace an object model (dff) and texture (txd) is stopped the object texture get white
-   Added ped pixel shaders
-   Added ability to layer multiple shaders on a world texture
-   Fixed Windows 8 missing dll error
-   Fixed [setElementPosition](/docs/setelementposition.md "wikilink") for vehicles on a non streamed in position will make the vehicle spin very quickly
-   Added check for GTA file loading failures
-   Fixed map editor crash
-   Fixed floating vehicles when using [setVehicleIdleRespawnDelay](/docs/setvehicleidlerespawndelay.md "wikilink")
-   Fixed [showhud](/docs/client_commands#showhud.md "wikilink") not fully working before the player has spawned
-   Fixed connect problem when using a domain name that starts with a number
-   Fixed missing font error message
-   Fixed [getSoundLength](/docs/getsoundlength.md "wikilink") returns 0 for sound streams (not radio streams)
-   Fixed a crash when taking a screenshot and minimizing then restoring
-   Fixed setElementFrozen killing players from falls
-   Fixed textures disappearing and flickering at certain camera angles

Server
------

### New Functions

-   Added [fetchRemote](/docs/fetchremote.md "wikilink")
-   Added [reloadBans](/docs/reloadbans.md "wikilink")
-   Added [getAllAccountData](/docs/getallaccountdata.md "wikilink")
-   Added [getLatentEventHandles](/docs/getlatenteventhandles.md "wikilink")
-   Added [getLatentEventStatus](/docs/getlatenteventstatus.md "wikilink")
-   Added [cancelLatentEvent](/docs/cancellatentevent.md "wikilink")
-   Added [removeVehicleSirens](/docs/removevehiclesirens.md "wikilink")
-   Added [getVehicleSirenParams](/docs/getvehiclesirenparams.md "wikilink")
-   Added [getVehicleSirens](/docs/getvehiclesirens.md "wikilink")
-   Added [setVehicleSirens](/docs/setvehiclesirens.md "wikilink")
-   Added [addVehicleSirens](/docs/addvehiclesirens.md "wikilink")
-   Added [setJetpackWeaponEnabled](/docs/setjetpackweaponenabled.md "wikilink")
-   Added [getJetpackWeaponEnabled](/docs/getjetpackweaponenabled.md "wikilink")
-   Added [fileCopy](/docs/filecopy.md "wikilink")

### New Events

-   None yet

### Changes / Bug Fixes

-   Fixed map files are downloading very slow issue
-   Fixed timeouts on map change
-   Tweaks and fixes for vehicle sync
-   Added order priority to [addEventHandler](/docs/addeventhandler.md "wikilink")
-   Improved performance when the server has a large number of IP bans
-   Added debug info to timers
-   Added adjustable sync rates to [setServerConfigSetting](/docs/setserverconfigsetting.md "wikilink") and the server config - Details: [Sync\_interval\_settings](/docs/sync_interval_settings.md "wikilink")
-   Fixed lightsync vehicles ghost streaming in when locally they are miles away
-   Fixed server sometimes not appearing in the browser
-   Added server setting to reduce CPU usage
-   Sped up event handling system for server and client
-   Tweaked server networking
-   Improved Lua errors for server element functions
-   Reduced CPU usage more
-   Made timers less crashy
-   Added vehicle extrapolation - Details: [mtaserver.conf -&gt; vehext\_](/docs/mtaserver.conf#vehext_percent.md "wikilink")
-   Fixed server crash when towing a clientside vehicle
-   Added option to suppress certain MySQL error messages
-   Sped up [triggerClientEvent](/docs/triggerclientevent.md "wikilink")
-   Made [setVehicleIdleRespawnDelay](/docs/setvehicleidlerespawndelay.md "wikilink") work for non-streamed in vehicles
-   Added logging for [callRemote](/docs/callremote.md "wikilink")
-   Large amount of other crashfixes, improvements and tweaks

Resources
---------

-   Updated parachute to fix high CPU usage on clients
-   Added Visualiser resource
-   Added GUI Siren Editor
-   Fixed a reload exploit where you could jump and then reload for an instant reload
-   Made reload with jetpack work again
-   Fixed freeroam bookmarks
-   Fixed some errors and warnings

Editor
------

-   Fixed Map editor not saving locations of objects on Linux machines
-   Added cancel option when starting map editor from menu
-   Added ability to change object and vehicle alpha
-   Changed vehicle color selection to use the new RGB color system
-   Fixed server settings tab in options not showing up when using Map Editor from main menu
-   Added ability to place peds
-   Added object scale option
-   Added object collisions option

[hu:Changes in 1.3.1](/docs/hu-changes_in_1.3.1.md "wikilink") [pt-br:Novidades na versão 1.3.1](/docs/pt-br-novidades_na_versão_1.3.1.md "wikilink") [ru:Changes in 1.3.1](/docs/ru-changes_in_1.3.1.md "wikilink")

[Category:Changes in 1.3](/docs/category-changes_in_1.3.md "wikilink")
