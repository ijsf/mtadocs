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

-   Added [setObjectBreakable](/docs/setObjectBreakable.md "wikilink")
-   Added [isObjectBreakable](/docs/isObjectBreakable.md "wikilink")
-   Added [dxSetBlendMode](/docs/dxSetBlendMode.md "wikilink")
-   Added [dxGetBlendMode](/docs/dxGetBlendMode.md "wikilink")
-   Added [dxDrawMaterialLine3D](/docs/dxDrawMaterialLine3D.md "wikilink")
-   Added [dxDrawMaterialSectionLine3D](/docs/dxDrawMaterialSectionLine3D.md "wikilink")
-   Added [getLatentEventHandles](/docs/getLatentEventHandles.md "wikilink")
-   Added [getLatentEventStatus](/docs/getLatentEventStatus.md "wikilink")
-   Added [cancelLatentEvent](/docs/cancelLatentEvent.md "wikilink")
-   Added [triggerLatentServerEvent](/docs/triggerLatentServerEvent.md "wikilink")
-   Added [getVehicleSirenParams](/docs/getVehicleSirenParams.md "wikilink")
-   Added [getVehicleSirens](/docs/getVehicleSirens.md "wikilink")
-   Added [setVehicleSirens](/docs/setVehicleSirens.md "wikilink")
-   Added [getSoundProperties](/docs/getSoundProperties.md "wikilink")
-   Added [setSoundProperties](/docs/setSoundProperties.md "wikilink")
-   Added [getSoundFFTData](/docs/getSoundFFTData.md "wikilink")
-   Added [setSoundPanningEnabled](/docs/setSoundPanningEnabled.md "wikilink")
-   Added [isSoundPanningEnabled](/docs/isSoundPanningEnabled.md "wikilink")
-   Added [setWorldSoundEnabled](/docs/setWorldSoundEnabled.md "wikilink")
-   Added [isWorldSoundEnabled](/docs/isWorldSoundEnabled.md "wikilink")
-   Added [resetWorldSounds](/docs/resetWorldSounds.md "wikilink")
-   Added [getSoundBPM](/docs/getSoundBPM.md "wikilink")
-   Added [getSoundLevelData](/docs/getSoundLevelData.md "wikilink")
-   Added [getSoundWaveData](/docs/getSoundWaveData.md "wikilink")
-   Added [setPedAnalogControlState](/docs/setPedAnalogControlState.md "wikilink")
-   Added [getPedAnalogControlState](/docs/getPedAnalogControlState.md "wikilink")
-   Added [setAnalogControlState](/docs/setAnalogControlState.md "wikilink")
-   Added [getAnalogControlState](/docs/getAnalogControlState.md "wikilink")
-   Added [setPedTargetingMarkerEnabled](/docs/setPedTargetingMarkerEnabled.md "wikilink")
-   Added [isPedTargetingMarkerEnabled](/docs/isPedTargetingMarkerEnabled.md "wikilink")
-   Added [setElementMatrix](/docs/setElementMatrix.md "wikilink")
-   Added [warpPedIntoVehicle](/docs/warpPedIntoVehicle.md "wikilink")
-   Added [removePedFromVehicle](/docs/removePedFromVehicle.md "wikilink")
-   Added [setProjectileCounter](/docs/setProjectileCounter.md "wikilink")
-   Added [createWeapon](/docs/createWeapon.md "wikilink")
-   Added [fireWeapon](/docs/fireWeapon.md "wikilink")
-   Added [setWeaponProperty](/docs/setWeaponProperty.md "wikilink")
-   Added [setWeaponState](/docs/setWeaponState.md "wikilink")
-   Added [setWeaponTarget](/docs/setWeaponTarget.md "wikilink")
-   Added [getWeaponOwner](/docs/getWeaponOwner.md "wikilink")
-   Added [setWeaponOwner](/docs/setWeaponOwner.md "wikilink")
-   Added [setWeaponFlags](/docs/setWeaponFlags.md "wikilink")
-   Added [getWeaponFlags](/docs/getWeaponFlags.md "wikilink")
-   Added [setWeaponFiringRate](/docs/setWeaponFiringRate.md "wikilink")
-   Added [getWeaponFiringRate](/docs/getWeaponFiringRate.md "wikilink")
-   Added [resetWeaponFiringRate](/docs/resetWeaponFiringRate.md "wikilink")
-   Added [getWeaponClipAmmo](/docs/getWeaponClipAmmo.md "wikilink")
-   Added [setWeaponClipAmmo](/docs/setWeaponClipAmmo.md "wikilink")
-   Added [getWeaponAmmo](/docs/getWeaponAmmo.md "wikilink")
-   Added [setWeaponAmmo](/docs/setWeaponAmmo.md "wikilink")
-   Added [getProjectileCounter](/docs/getProjectileCounter.md "wikilink")
-   Added [setWaterDrawnLast](/docs/setWaterDrawnLast.md "wikilink")
-   Added [isWaterDrawnLast](/docs/isWaterDrawnLast.md "wikilink")
-   Added [guiLabelGetColor](/docs/guiLabelGetColor.md "wikilink")

### New Events

-   Added [onClientPedHeliKilled](/docs/onClientPedHeliKilled.md "wikilink")
-   Added [onClientPlayerHeliKilled](/docs/onClientPlayerHeliKilled.md "wikilink")
-   Added [onClientPlayerHitByWaterCannon](/docs/onClientPlayerHitByWaterCannon.md "wikilink")
-   Added [onClientPedHitByWaterCannon](/docs/onClientPedHitByWaterCannon.md "wikilink")
-   Added [onClientPlayerPickupHit](/docs/onClientPlayerPickupHit.md "wikilink")
-   Added [onClientPlayerPickupLeave](/docs/onClientPlayerPickupLeave.md "wikilink")
-   Added [onClientSoundBeat](/docs/onClientSoundBeat.md "wikilink")
-   Added [onClientWeaponFire](/docs/onClientWeaponFire.md "wikilink")

### Changes / Bug Fixes

-   Fixed 'not being able to enter vehicles' bug
-   Added order priority to [addEventHandler](/docs/addEventHandler.md "wikilink")
-   Fixed 'engineless' NRG-500 Variant
-   Added option to skip Dual Monitor Resolution Select
-   Made [playSound3D](/docs/playSound3D.md "wikilink") use the camera position instead of the player position when determining the distance
-   Added color coding and sub-pixel positioning options to [dxDrawText](/docs/dxDrawText.md "wikilink")
-   Added ability to create and modify cubemaps and volume textures - Details: [dxCreateTexture](/docs/dxCreateTexture.md "wikilink")
-   Added model cache system to reduce loading delays
-   Added CJ clothes cache to help reduce game freezes
-   Sped up event handling system for server and client
-   Added element option to [engineApplyShaderToWorldTexture](/docs/engineApplyShaderToWorldTexture.md "wikilink")
-   Added optional bool to [getElementMatrix](/docs/getElementMatrix.md "wikilink") ( element, bool )
-   Added unrar for smoother update procedure
-   Fixed custom model replacement errors sometimes with weapons & weapon pickups.
-   Fixed vehicle upgrade custom models not showing immediately
-   Fixed accuracy of hit point in [onClientPlayerWeaponFire](/docs/onClientPlayerWeaponFire.md "wikilink") and added shot origin parameter
-   Fixed [setPedAimTarget](/docs/setPedAimTarget.md "wikilink") direction being all wrong
-   Fixed issue when peds' bullets origin from wrong position
-   Fixed custom models not rendering correctly sometimes parameter
-   Fixed custom model LOD distance is not reseting after quiting
-   Added size limit for clientscript.log file
-   Added ability to shoot with any weapon with jetpack
-   Made timers less crashy
-   Fixed some animation crashes
-   Fixed [getPedMoveState](/docs/getPedMoveState.md "wikilink") returns false when moving in crouch state
-   Fixed a bug when a resource that replace an object model (dff) and texture (txd) is stopped the object texture get white
-   Added ped pixel shaders
-   Added ability to layer multiple shaders on a world texture
-   Fixed Windows 8 missing dll error
-   Fixed [setElementPosition](/docs/setElementPosition.md "wikilink") for vehicles on a non streamed in position will make the vehicle spin very quickly
-   Added check for GTA file loading failures
-   Fixed map editor crash
-   Fixed floating vehicles when using [setVehicleIdleRespawnDelay](/docs/setVehicleIdleRespawnDelay.md "wikilink")
-   Fixed [showhud](/docs/Client_Commands#showhud.md "wikilink") not fully working before the player has spawned
-   Fixed connect problem when using a domain name that starts with a number
-   Fixed missing font error message
-   Fixed [getSoundLength](/docs/getSoundLength.md "wikilink") returns 0 for sound streams (not radio streams)
-   Fixed a crash when taking a screenshot and minimizing then restoring
-   Fixed setElementFrozen killing players from falls
-   Fixed textures disappearing and flickering at certain camera angles

Server
------

### New Functions

-   Added [fetchRemote](/docs/fetchRemote.md "wikilink")
-   Added [reloadBans](/docs/reloadBans.md "wikilink")
-   Added [getAllAccountData](/docs/getAllAccountData.md "wikilink")
-   Added [getLatentEventHandles](/docs/getLatentEventHandles.md "wikilink")
-   Added [getLatentEventStatus](/docs/getLatentEventStatus.md "wikilink")
-   Added [cancelLatentEvent](/docs/cancelLatentEvent.md "wikilink")
-   Added [removeVehicleSirens](/docs/removeVehicleSirens.md "wikilink")
-   Added [getVehicleSirenParams](/docs/getVehicleSirenParams.md "wikilink")
-   Added [getVehicleSirens](/docs/getVehicleSirens.md "wikilink")
-   Added [setVehicleSirens](/docs/setVehicleSirens.md "wikilink")
-   Added [addVehicleSirens](/docs/addVehicleSirens.md "wikilink")
-   Added [setJetpackWeaponEnabled](/docs/setJetpackWeaponEnabled.md "wikilink")
-   Added [getJetpackWeaponEnabled](/docs/getJetpackWeaponEnabled.md "wikilink")
-   Added [fileCopy](/docs/fileCopy.md "wikilink")

### New Events

-   None yet

### Changes / Bug Fixes

-   Fixed map files are downloading very slow issue
-   Fixed timeouts on map change
-   Tweaks and fixes for vehicle sync
-   Added order priority to [addEventHandler](/docs/addEventHandler.md "wikilink")
-   Improved performance when the server has a large number of IP bans
-   Added debug info to timers
-   Added adjustable sync rates to [setServerConfigSetting](/docs/setServerConfigSetting.md "wikilink") and the server config - Details: [Sync\_interval\_settings](/Sync_interval_settings.md "wikilink")
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
-   Sped up [triggerClientEvent](/docs/triggerClientEvent.md "wikilink")
-   Made [setVehicleIdleRespawnDelay](/docs/setVehicleIdleRespawnDelay.md "wikilink") work for non-streamed in vehicles
-   Added logging for [callRemote](/docs/callRemote.md "wikilink")
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

[hu:Changes in 1.3.1](/docs/hu:Changes_in_1.3.1.md "wikilink") [pt-br:Novidades na versão 1.3.1](/pt-br:Novidades_na_versão_1.3.1.md "wikilink") [ru:Changes in 1.3.1](/ru:Changes_in_1.3.1.md "wikilink")

[Category:Changes in 1.3](/docs/Category:Changes_in_1.3.md "wikilink")
