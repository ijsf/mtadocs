This page lists all changes which may be relevant to scripters and end users. Any changes which were back ported to 1.0.x have not been listed here. If you know of any changes that need mentioning feel free to update the list as the original author of this page does not understand every commit made (he isn't a developer)

End-user features
-----------------

**Very incomplete list**

-   Vehicle handling can be modified by servers
-   Custom fonts
-   Special skins
-   Improved server browser
-   Voice chat (on servers that support it)
-   Improved sound support, including streaming audio
-   Increased maximum player count
-   Custom shaders
-   Cars can now have any color you want, not just the ones GTA has normally
-   GUI Skin switching

Client
------

### New Functions

-   Added [guiCreateComboBox](/guiCreateComboBox.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1815>
-   Added [guiComboBoxAddItem](/guiComboBoxAddItem.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1815>
-   Added [guiComboBoxGetItemText](/guiComboBoxGetItemText.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1815>
-   Added [guiComboBoxSetItemText](/guiComboBoxSetItemText.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1815>
-   Added [guiComboBoxRemoveItem](/guiComboBoxRemoveItem.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1815>
-   Added [guiComboBoxGetSelected](/guiComboBoxGetSelected.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1815>
-   Added [guiComboBoxSetSelected](/guiComboBoxSetSelected.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1815>
-   Added [getPedMoveState](/getPedMoveState.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1842>
-   Added [getCameraViewMode](/getCameraViewMode.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1861>
-   Added [setCameraViewMode](/setCameraViewMode.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1861>
-   Added [resetTimer](/resetTimer.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1876>
-   Added [getSoundMetaTags](/getSoundMetaTags.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1755>
-   Added [getSoundEffects](/getSoundEffects.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1755>
-   Added [setSoundEffectEnabled](/setSoundEffectEnabled.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1755>
-   Added [getElementAttachedOffsets](/getElementAttachedOffsets.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1899>
-   Added [setTrafficLightState](/setTrafficLightState.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1836>
-   Added [getTrafficLightState](/getTrafficLightState.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1836>
-   Added [utfChar](/utfChar.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1944>
-   Added [utfCode](/utfCode.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1944>
-   Added [utfLen](/utfLen.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1944>
-   Added [utfSeek](/utfSeek.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1944>
-   Added [utfSub](/utfSub.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1944>
-   Added [fileClose](/fileClose.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1975>
-   Added [fileCreate](/fileCreate.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1975>
-   Added [fileDelete](/fileDelete.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1975>
-   Added [fileExists](/fileExists.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1975>
-   Added [fileFlush](/fileFlush.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1975>
-   Added [fileGetPos](/fileGetPos.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1975>
-   Added [fileGetSize](/fileGetSize.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1975>
-   Added [fileIsEOF](/fileIsEOF.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1975>
-   Added [fileOpen](/fileOpen.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1975>
-   Added [fileRead](/fileRead.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1975>
-   Added [fileRename](/fileRename.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1975>
-   Added [fileSetPos](/fileSetPos.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1975>
-   Added [fileWrite](/fileWrite.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1975>
-   Added [fileRename](/fileRename.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2611>
-   Added [setVehicleTurretPosition](/setVehicleTurretPosition.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1996>
-   Added [getResourceExportedFunctions](/getResourceExportedFunctions.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1998>
-   Added [getCameraGoggleEffect](/getCameraGoggleEffect.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2032>
-   Added [setCameraGoggleEffect](/setCameraGoggleEffect.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2032>
-   Added [getPlayerSerial](/getPlayerSerial.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2052>
-   Added [getWindVelocity](/getWindVelocity.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2072>
-   Added [setWindVelocity](/setWindVelocity.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2072>
-   Added [resetWindVelocity](/resetWindVelocity.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2072>
-   Added [guiSetInputMode](/guiSetInputMode.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2075>
-   Added [guiGetInputMode](/guiGetInputMode.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2075>
-   Added [getWaterColor](/getWaterColor.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2092>
-   Added [getSkyGradient](/getSkyGradient.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2093>
-   Added [setElementFrozen](/setElementFrozen.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2096>
-   Added [isElementFrozen](/isElementFrozen.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2096>
-   Added [getInteriorSoundsEnabled](/getInteriorSoundsEnabled.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2100>
-   Added [setInteriorSoundsEnabled](/setInteriorSoundsEnabled.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2100>
-   Added [getRainLevel](/getRainLevel.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2103>
-   Added [setRainLevel](/setRainLevel.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2103>
-   Added [resetRainLevel](/resetRainLevel.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2103>
-   Added [getFogDistance](/getFogDistance.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2104>
-   Added [setFogDistance](/setFogDistance.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2104>
-   Added [resetFogDistance](/resetFogDistance.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2104>
-   Added [getEasingValue](/getEasingValue.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2122>
-   Added [interpolateBetween](/interpolateBetween.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2122>
-   Added [getSunColor](/getSunColor.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2134>
-   Added [setSunColor](/setSunColor.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2134>
-   Added [resetSunColor](/resetSunColor.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2134>
-   Added [getSunSize](/getSunSize.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2135>
-   Added [setSunSize](/setSunSize.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2135>
-   Added [resetSunSize](/resetSunSize.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2135>
-   Added [setElementID](/setElementID.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2154>
-   Added [getBlipVisibleDistance](/getBlipVisibleDistance.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2248>
-   Added [setBlipVisibleDistance](/setBlipVisibleDistance.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2248>
-   Added [setVehicleDoorOpenRatio](/setVehicleDoorOpenRatio.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2329>
-   Added [getVehicleDoorOpenRatio](/getVehicleDoorOpenRatio.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2329>
-   Added [getHeatHaze](/getHeatHaze.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2349>
-   Added [setHeatHaze](/setHeatHaze.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2349>
-   Added [resetHeatHaze](/resetHeatHaze.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2349>
-   Added [setClipBoard](/setClipBoard.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2517>
-   Added [dxCreateTexture](/dxCreateTexture.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2796>
-   Added [dxCreateShader](/dxCreateShader.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2796>
-   Added [dxSetShaderValue](/dxSetShaderValue.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2796>
-   Added [dxCreateRenderTarget](/dxCreateRenderTarget.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2797>
-   Added [dxSetRenderTarget](/dxSetRenderTarget.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2797>
-   Added [dxCreateScreenSource](/dxCreateScreenSource.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2797>
-   Added [dxUpdateScreenSource](/dxUpdateScreenSource.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2797>
-   Added [dxGetMaterialSize](/dxGetMaterialSize.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2797>
-   Added [dxCreateFont](/dxCreateFont.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2814>
-   Added [guiCreateFont](/guiCreateFont.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2814>
-   Added [engineApplyShaderToModel](/engineApplyShaderToModel.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2828>
-   Added [engineRemoveShaderFromModel](/engineRemoveShaderFromModel.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2828>
-   Added [engineGetModelNameFromID](/engineGetModelNameFromID.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2843>
-   Added [engineGetModelIDFromName](/engineGetModelIDFromName.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2843>
-   Added [setAircraftMaxHeight](/setAircraftMaxHeight.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2848>
-   Added [detonateSatchels](/detonateSatchels.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2857>
-   Added [engineApplyShaderToWorldTexture](/engineApplyShaderToWorldTexture.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2888>
-   Added [engineGetModelTextureNames](/engineGetModelTextureNames.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2892>
-   Added [setAmbientSoundEnabled](/setAmbientSoundEnabled.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2905>
-   Added [isAmbientSoundEnabled](/isAmbientSoundEnabled.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2905>
-   Added [resetAmbientSounds](/resetAmbientSounds.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2905>
-   Added [getJetpackMaxHeight](/getJetpackMaxHeight.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2084>
-   Added [setJetpackMaxHeight](/setJetpackMaxHeight.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2084>
-   Added [getNetworkStats](/getNetworkStats.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2979>
-   Added [setPedAnimationProgress](/setPedAnimationProgress.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=3002>
-   Added [dxGetStatus](/dxGetStatus.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=3041>
-   Added [dxSetTestMode](/dxSetTestMode.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=3041>

### New Events

-   Added [onClientDoubleClick](/onClientDoubleClick.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1808>
-   Added [onClientGUIComboBoxAccepted](/onClientGUIComboBoxAccepted.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1846>
-   Added [onClientSoundStream](/onClientSoundStream.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1755>
-   Added [onClientSoundChangedMeta](/onClientSoundChangedMeta.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1898>
-   Added [onClientSoundFinishedDownload](/onClientSoundFinishedDownload.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1755>
-   Added [onClientVehicleExplode](/onClientVehicleExplode.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1906>
-   Added [onClientGUIFocus](/onClientGUIFocus.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2075>
-   Added [onClientGUIBlur](/onClientGUIBlur.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2075>
-   Added [onClientDebugMessage](/onClientDebugMessage.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2091>
-   Added [onClientKey](/onClientKey.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2480>
-   Added [onClientCharacter](/onClientCharacter.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2480>
-   Added [onClientHUDRender](/onClientHUDRender.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2855>
-   Added [onClientMinimize](/onClientMinimize.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2945>
-   Added [onClientRestore](/onClientRestore.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2945>

### Changes

-   Improved [setPedAnimation](/setPedAnimation.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1763>
-   Added server join que Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1828>
-   Made knife kills more balanced Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1839>
-   Fixed water elements being affected by [resetMapInfo](/resetMapInfo.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1863>
-   Made [onClientPlayerVehicleExit](/onClientPlayerVehicleExit.md "wikilink") more reliable Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1877>
-   Added BASS (allows stream files to be played) Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1755>
-   Added synchronized traffic lights Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1836>
-   Added “all” to [showPlayerHudComponent](/showPlayerHudComponent.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1912>
-   Added “crosshair” to [showPlayerHudComponent](/showPlayerHudComponent.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2974>
-   Added “radio” and “wanted” to [showPlayerHudComponent](/showPlayerHudComponent.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2027>
-   Added support for unicode text Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1944>
-   Added RGB vehicle colors Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2090>
-   Synchronized vehicle doors Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2110>
-   Added localPlayer predefined variable Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2140>
-   Made [onClientPlayerWasted](/onClientPlayerWasted.md "wikilink") work for the local player Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2180>
-   Added special skins to the game Details: <http://wiki.multitheftauto.com/wiki/Special_Skins_Page>
-   Added new main menu starting at: <http://code.google.com/p/mtasa-blue/source/detail?r=2280>
-   Added GUI skin changer Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2308>
-   Added basic sync for objects Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2312>
-   Made game loading when joining a server much quicker Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2325>
-   Added new server browser starting at: <http://code.google.com/p/mtasa-blue/source/detail?r=2441>
-   Renamed hud command to showhud Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2566>
-   Added random name generator Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2582>
-   Added custom handling to vehicles Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2678>
-   Increased the available streamer memory Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2740>
-   Added shader element for [dxDrawImage](/dxDrawImage.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2790>
-   New message box images Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2793>
-   split and gettok no longer require string.byte Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2808>
-   Added world model info to [processLineOfSight](/processLineOfSight.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2845>
-   Added default buttons in settings Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2864>
-   Disabled brown streak trailer Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2880>
-   Large amount of crash fixes, bug fixes and optimizations
-   Added ability to add shaders to the game
-   Changed [guiGridListSetItemData](/guiGridListSetItemData.md "wikilink") to support any datatype <http://code.google.com/p/mtasa-blue/source/detail?r=2005>
-   Added voice (microphone support) to the game <http://code.google.com/p/mtasa-blue/source/detail?r=3000>

Server
------

### New Functions

-   Added [getElementAttachedOffsets](/getElementAttachedOffsets.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1899>
-   Added [setTrafficLightsLocked](/setTrafficLightsLocked.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1836>
-   Added [areTrafficLightsLocked](/areTrafficLightsLocked.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1836>
-   Added [utfChar](/utfChar.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1944>
-   Added [utfCode](/utfCode.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1944>
-   Added [utfLen](/utfLen.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1944>
-   Added [utfSeek](/utfSeek.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1944>
-   Added [utfSub](/utfSub.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1944>
-   Added [refreshResources](/refreshResources.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1994>
-   Added [setVehicleTurretPosition](/setVehicleTurretPosition.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1996>
-   Added [getObjectScale](/getObjectScale.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2029>
-   Added [setObjectScale](/setObjectScale.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2029>
-   Added [setElementCollisionsEnabled](/setElementCollisionsEnabled.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2030>
-   Added [getElementCollisionsEnabled](/getElementCollisionsEnabled.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2030>
-   Added [setWaterColor](/setWaterColor.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2092>
-   Added [getWaterColor](/getWaterColor.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2092>
-   Added [getSkyGradient](/getSkyGradient.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2093>
-   Added [setElementFrozen](/setElementFrozen.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2096>
-   Added [isElementFrozen](/isElementFrozen.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2096>
-   Added [getEasingValue](/getEasingValue.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2122>
-   Added [interpolateBetween](/interpolateBetween.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2122>
-   Added [getBlipVisibleDistance](/getBlipVisibleDistance.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2248>
-   Added [setBlipVisibleDistance](/setBlipVisibleDistance.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2248>
-   Added [getNetworkUsageData](/getNetworkUsageData.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2322>
-   Added [setVehicleDoorOpenRatio](/setVehicleDoorOpenRatio.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2329>
-   Added [getVehicleDoorOpenRatio](/getVehicleDoorOpenRatio.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2329>
-   Added [getHeatHaze](/getHeatHaze.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2349>
-   Added [setHeatHaze](/setHeatHaze.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2349>
-   Added [resetHeatHaze](/resetHeatHaze.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2349>
-   Added [getInteriorSoundsEnabled](/getInteriorSoundsEnabled.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2449>
-   Added [setInteriorSoundsEnabled](/setInteriorSoundsEnabled.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2449>
-   Added [getRainLevel](/getRainLevel.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2449>
-   Added [setRainLevel](/setRainLevel.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2449>
-   Added [resetRainLevel](/resetRainLevel.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2449>
-   Added [getSunSize](/getSunSize.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2449>
-   Added [setSunSize](/setSunSize.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2449>
-   Added [resetSunSize](/resetSunSize.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2449>
-   Added [getSunColor](/getSunColor.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2449>
-   Added [setSunColor](/setSunColor.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2449>
-   Added [resetSunColor](/resetSunColor.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2449>
-   Added [getWindVelocity](/getWindVelocity.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2449>
-   Added [setWindVelocity](/setWindVelocity.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2449>
-   Added [resetWindVelocity](/resetWindVelocity.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2449>
-   Added [getFarClipDistance](/getFarClipDistance.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2449>
-   Added [setFarClipDistance](/setFarClipDistance.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2449>
-   Added [resetFarClipDistance](/resetFarClipDistance.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2449>
-   Added [getFogDistance](/getFogDistance.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2449>
-   Added [setFogDistance](/setFogDistance.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2449>
-   Added [resetFogDistance](/resetFogDistance.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2449>
-   Added [fileRename](/fileRename.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2611>
-   Added [detonatePlayerSatchels](/detonatePlayerSatchels.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2857>
-   Added [setMaxPlayers](/setMaxPlayers.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2941>
-   Added [getServerConfigSetting](/getServerConfigSetting.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2971>
-   Added [setServerConfigSetting](/setServerConfigSetting.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2971>
-   Added [getJetpackMaxHeight](/getJetpackMaxHeight.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2084>
-   Added [getAircraftMaxHeight](/getAircraftMaxHeight.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2975>
-   Added [setAircraftMaxHeight](/setAircraftMaxHeight.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2975>
-   Added [getNetworkStats](/getNetworkStats.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2979>
-   Added [setPedAnimationProgress](/setPedAnimationProgress.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=3002>
-   Added [setPlayerVoiceIgnoreFrom](/setPlayerVoiceIgnoreFrom.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=3042>
-   Added [setPlayerVoiceBroadcastTo](/setPlayerVoiceBroadcastTo.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=3000>

### New Events

-   Added [onPlayerMute](/onPlayerMute.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1978>
-   Added [onPlayerUnmute](/onPlayerUnmute.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1978>
-   Added [onDebugMessage](/onDebugMessage.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2091>
-   Added [onSettingChange](/onSettingChange.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2097>
-   Added [onPlayerCommand](/onPlayerCommand.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2152>
-   Added [onAccountDataChange](/onAccountDataChange.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2516>
-   Added [onPlayerModInfo](/onPlayerModInfo.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2881>

### Changes

-   Fixed [isElementInWater](/isElementInWater.md "wikilink") with unoccupied vehicles Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1803>
-   Allowed responsible element of [kickPlayer](/kickPlayer.md "wikilink") be a string Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1979>
-   Allowed responsible element of [banPlayer](/banPlayer.md "wikilink")/[addBan](/addBan.md "wikilink") be a string Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1980>
-   Added “all” to [showPlayerHudComponent](/showPlayerHudComponent.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=1912>
-   Added “radio” and “wanted” to [showPlayerHudComponent](/showPlayerHudComponent.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2027>
-   Added optional type to [aclListRights](/aclListRights.md "wikilink") Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2036>
-   Updated [setVehicleColor](/setVehicleColor.md "wikilink") and [getVehicleColor](/getVehicleColor.md "wikilink") to support RGB vehicle colors
-   Raised max player count to 65535 Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2118>
-   Made [onPlayerWeaponSwitch](/onPlayerWeaponSwitch.md "wikilink") work Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2137>
-   Rotation parameter in [createPed](/createPed.md "wikilink") now works Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2246>
-   Added resources cataloges (\[likethis\]) Starting at: <http://code.google.com/p/mtasa-blue/source/detail?r=2716>
-   [split](/split.md "wikilink") and [gettok](/gettok.md "wikilink") no longer require string.byte Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2808>
-   Added bandwidth stats to performance browser Details: <http://code.google.com/p/mtasa-blue/source/detail?r=2901>
-   Added bandwidth reduction options Details: <http://code.google.com/p/mtasa-blue/source/detail?r=3028>
-   Large amount of crash fixes, bug fixes and optimizations

Resources
---------

-   Removed set blur from admin due to it causing conflicts with other gamemodes
-   Fixed a variety of debug warnings and errors in resources
-   Players can no longer capture the vehicle in an enemy base in CTV gamemode
-   Fixed a problem in the maplimits resource causing performance problems over time
-   Added HTTP runcode interface
-   Changed resources structure to use the \[catalog\] system
-   Added RGB vehicle colors and headlight colors to freeroam
-   Upgraded from newly deprecated functions setPedFrozen and setVehicleFrozen
-   Make play resource give out new special skins
-   Removed redundant localPlayer defines as already predefined in 1.1
-   Encoded all resources in UTF-8
-   Added special skins to freeroam
-   Improved reliability of admin flags
-   Fixed stats reset after a respawn with default stats
-   Improved reliability of parachutes
-   Sped up map ratings resource
-   Improvements to performancebrowser resource
-   Fixed resourcebrowser display problems in IE
-   Made it easier to close the freeroam spawn selector
-   Fixed lag during startup of admin
-   Added normal dates to resourcemanager
-   Fixed lag caused by country flags

Map Editor
----------

-   Added a loading bar when loading a map is taking a long time
-   Added basic test mode to allow single players to test their map without starting test
-   Fixed object position and rotation not saving if selected during the save
-   Added trains to the Map Editor
-   Fixed some element attributes not cloning with clone element
-   Made map settings function in test mode
-   Added trailers to the Map Editor
-   Added various safety checks to saving and loading
-   Added option to clone world buildings
-   Fixed a bug when not being able to open maps

[Category:Changelog](/Category:Changelog.md "wikilink") [Category:Changes in 1.1](/Category:Changes_in_1.1.md "wikilink")
