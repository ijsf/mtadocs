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

-   Added [setObjectBreakable](/setObjectBreakable.md "wikilink")
-   Added [isObjectBreakable](/isObjectBreakable.md "wikilink")
-   Added [dxSetBlendMode](/dxSetBlendMode.md "wikilink")
-   Added [dxGetBlendMode](/dxGetBlendMode.md "wikilink")
-   Added [dxDrawMaterialLine3D](/dxDrawMaterialLine3D.md "wikilink")
-   Added [dxDrawMaterialSectionLine3D](/dxDrawMaterialSectionLine3D.md "wikilink")
-   Added [getLatentEventHandles](/getLatentEventHandles.md "wikilink")
-   Added [getLatentEventStatus](/getLatentEventStatus.md "wikilink")
-   Added [cancelLatentEvent](/cancelLatentEvent.md "wikilink")
-   Added [triggerLatentServerEvent](/triggerLatentServerEvent.md "wikilink")
-   Added [getVehicleSirenParams](/getVehicleSirenParams.md "wikilink")
-   Added [getVehicleSirens](/getVehicleSirens.md "wikilink")
-   Added [setVehicleSirens](/setVehicleSirens.md "wikilink")
-   Added [getSoundProperties](/getSoundProperties.md "wikilink")
-   Added [setSoundProperties](/setSoundProperties.md "wikilink")
-   Added [getSoundFFTData](/getSoundFFTData.md "wikilink")
-   Added [setSoundPanningEnabled](/setSoundPanningEnabled.md "wikilink")
-   Added [isSoundPanningEnabled](/isSoundPanningEnabled.md "wikilink")
-   Added [setWorldSoundEnabled](/setWorldSoundEnabled.md "wikilink")
-   Added [isWorldSoundEnabled](/isWorldSoundEnabled.md "wikilink")
-   Added [resetWorldSounds](/resetWorldSounds.md "wikilink")
-   Added [getSoundBPM](/getSoundBPM.md "wikilink")
-   Added [getSoundLevelData](/getSoundLevelData.md "wikilink")
-   Added [getSoundWaveData](/getSoundWaveData.md "wikilink")
-   Added [setPedAnalogControlState](/setPedAnalogControlState.md "wikilink")
-   Added [getPedAnalogControlState](/getPedAnalogControlState.md "wikilink")
-   Added [setAnalogControlState](/setAnalogControlState.md "wikilink")
-   Added [getAnalogControlState](/getAnalogControlState.md "wikilink")
-   Added [setPedTargetingMarkerEnabled](/setPedTargetingMarkerEnabled.md "wikilink")
-   Added [isPedTargetingMarkerEnabled](/isPedTargetingMarkerEnabled.md "wikilink")
-   Added [setElementMatrix](/setElementMatrix.md "wikilink")
-   Added [warpPedIntoVehicle](/warpPedIntoVehicle.md "wikilink")
-   Added [removePedFromVehicle](/removePedFromVehicle.md "wikilink")
-   Added [setProjectileCounter](/setProjectileCounter.md "wikilink")
-   Added [createWeapon](/createWeapon.md "wikilink")
-   Added [fireWeapon](/fireWeapon.md "wikilink")
-   Added [setWeaponProperty](/setWeaponProperty.md "wikilink")
-   Added [setWeaponState](/setWeaponState.md "wikilink")
-   Added [setWeaponTarget](/setWeaponTarget.md "wikilink")
-   Added [getWeaponOwner](/getWeaponOwner.md "wikilink")
-   Added [setWeaponOwner](/setWeaponOwner.md "wikilink")
-   Added [setWeaponFlags](/setWeaponFlags.md "wikilink")
-   Added [getWeaponFlags](/getWeaponFlags.md "wikilink")
-   Added [setWeaponFiringRate](/setWeaponFiringRate.md "wikilink")
-   Added [getWeaponFiringRate](/getWeaponFiringRate.md "wikilink")
-   Added [resetWeaponFiringRate](/resetWeaponFiringRate.md "wikilink")
-   Added [getWeaponClipAmmo](/getWeaponClipAmmo.md "wikilink")
-   Added [setWeaponClipAmmo](/setWeaponClipAmmo.md "wikilink")
-   Added [getWeaponAmmo](/getWeaponAmmo.md "wikilink")
-   Added [setWeaponAmmo](/setWeaponAmmo.md "wikilink")
-   Added [getProjectileCounter](/getProjectileCounter.md "wikilink")
-   Added [setWaterDrawnLast](/setWaterDrawnLast.md "wikilink")
-   Added [isWaterDrawnLast](/isWaterDrawnLast.md "wikilink")
-   Added [guiLabelGetColor](/guiLabelGetColor.md "wikilink")

### New Events

-   Added [onClientPedHeliKilled](/onClientPedHeliKilled.md "wikilink")
-   Added [onClientPlayerHeliKilled](/onClientPlayerHeliKilled.md "wikilink")
-   Added [onClientPlayerHitByWaterCannon](/onClientPlayerHitByWaterCannon.md "wikilink")
-   Added [onClientPedHitByWaterCannon](/onClientPedHitByWaterCannon.md "wikilink")
-   Added [onClientPlayerPickupHit](/onClientPlayerPickupHit.md "wikilink")
-   Added [onClientPlayerPickupLeave](/onClientPlayerPickupLeave.md "wikilink")
-   Added [onClientSoundBeat](/onClientSoundBeat.md "wikilink")
-   Added [onClientWeaponFire](/onClientWeaponFire.md "wikilink")

### Changes / Bug Fixes

-   Fixed 'not being able to enter vehicles' bug
-   Added order priority to [addEventHandler](/addEventHandler.md "wikilink")
-   Fixed 'engineless' NRG-500 Variant
-   Added option to skip Dual Monitor Resolution Select
-   Made [playSound3D](/playSound3D.md "wikilink") use the camera position instead of the player position when determining the distance
-   Added color coding and sub-pixel positioning options to [dxDrawText](/dxDrawText.md "wikilink")
-   Added ability to create and modify cubemaps and volume textures - Details: [dxCreateTexture](/dxCreateTexture.md "wikilink")
-   Added model cache system to reduce loading delays
-   Added CJ clothes cache to help reduce game freezes
-   Sped up event handling system for server and client
-   Added element option to [engineApplyShaderToWorldTexture](/engineApplyShaderToWorldTexture.md "wikilink")
-   Added optional bool to [getElementMatrix](/getElementMatrix.md "wikilink") ( element, bool )
-   Added unrar for smoother update procedure
-   Fixed custom model replacement errors sometimes with weapons & weapon pickups.
-   Fixed vehicle upgrade custom models not showing immediately
-   Fixed accuracy of hit point in [onClientPlayerWeaponFire](/onClientPlayerWeaponFire.md "wikilink") and added shot origin parameter
-   Fixed [setPedAimTarget](/setPedAimTarget.md "wikilink") direction being all wrong
-   Fixed issue when peds' bullets origin from wrong position
-   Fixed custom models not rendering correctly sometimes parameter
-   Fixed custom model LOD distance is not reseting after quiting
-   Added size limit for clientscript.log file
-   Added ability to shoot with any weapon with jetpack
-   Made timers less crashy
-   Fixed some animation crashes
-   Fixed [getPedMoveState](/getPedMoveState.md "wikilink") returns false when moving in crouch state
-   Fixed a bug when a resource that replace an object model (dff) and texture (txd) is stopped the object texture get white
-   Added ped pixel shaders
-   Added ability to layer multiple shaders on a world texture
-   Fixed Windows 8 missing dll error
-   Fixed [setElementPosition](/setElementPosition.md "wikilink") for vehicles on a non streamed in position will make the vehicle spin very quickly
-   Added check for GTA file loading failures
-   Fixed map editor crash
-   Fixed floating vehicles when using [setVehicleIdleRespawnDelay](/setVehicleIdleRespawnDelay.md "wikilink")
-   Fixed [showhud](/Client_Commands#showhud.md "wikilink") not fully working before the player has spawned
-   Fixed connect problem when using a domain name that starts with a number
-   Fixed missing font error message
-   Fixed [getSoundLength](/getSoundLength.md "wikilink") returns 0 for sound streams (not radio streams)
-   Fixed a crash when taking a screenshot and minimizing then restoring
-   Fixed setElementFrozen killing players from falls
-   Fixed textures disappearing and flickering at certain camera angles

Server
------

### New Functions

-   Added [fetchRemote](/fetchRemote.md "wikilink")
-   Added [reloadBans](/reloadBans.md "wikilink")
-   Added [getAllAccountData](/getAllAccountData.md "wikilink")
-   Added [getLatentEventHandles](/getLatentEventHandles.md "wikilink")
-   Added [getLatentEventStatus](/getLatentEventStatus.md "wikilink")
-   Added [cancelLatentEvent](/cancelLatentEvent.md "wikilink")
-   Added [removeVehicleSirens](/removeVehicleSirens.md "wikilink")
-   Added [getVehicleSirenParams](/getVehicleSirenParams.md "wikilink")
-   Added [getVehicleSirens](/getVehicleSirens.md "wikilink")
-   Added [setVehicleSirens](/setVehicleSirens.md "wikilink")
-   Added [addVehicleSirens](/addVehicleSirens.md "wikilink")
-   Added [setJetpackWeaponEnabled](/setJetpackWeaponEnabled.md "wikilink")
-   Added [getJetpackWeaponEnabled](/getJetpackWeaponEnabled.md "wikilink")
-   Added [fileCopy](/fileCopy.md "wikilink")

### New Events

-   None yet

### Changes / Bug Fixes

-   Fixed map files are downloading very slow issue
-   Fixed timeouts on map change
-   Tweaks and fixes for vehicle sync
-   Added order priority to [addEventHandler](/addEventHandler.md "wikilink")
-   Improved performance when the server has a large number of IP bans
-   Added debug info to timers
-   Added adjustable sync rates to [setServerConfigSetting](/setServerConfigSetting.md "wikilink") and the server config - Details: [Sync\_interval\_settings](/Sync_interval_settings.md "wikilink")
-   Fixed lightsync vehicles ghost streaming in when locally they are miles away
-   Fixed server sometimes not appearing in the browser
-   Added server setting to reduce CPU usage
-   Sped up event handling system for server and client
-   Tweaked server networking
-   Improved Lua errors for server element functions
-   Reduced CPU usage more
-   Made timers less crashy
-   Added vehicle extrapolation - Details: [mtaserver.conf -&gt; vehext\_](/mtaserver.conf#vehext_percent.md "wikilink")
-   Fixed server crash when towing a clientside vehicle
-   Added option to suppress certain MySQL error messages
-   Sped up [triggerClientEvent](/triggerClientEvent.md "wikilink")
-   Made [setVehicleIdleRespawnDelay](/setVehicleIdleRespawnDelay.md "wikilink") work for non-streamed in vehicles
-   Added logging for [callRemote](/callRemote.md "wikilink")
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

[hu:Changes in 1.3.1](/hu:Changes_in_1.3.1.md "wikilink") [pt-br:Novidades na versão 1.3.1](/pt-br:Novidades_na_versão_1.3.1.md "wikilink") [ru:Changes in 1.3.1](/ru:Changes_in_1.3.1.md "wikilink")

[Category:Changes in 1.3](/Category:Changes_in_1.3.md "wikilink")
