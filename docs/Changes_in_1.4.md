Main Additions / Changes
------------------------

-   Localization of MTA's menus
-   [OOP](/OOP.md "wikilink") classes
-   [Matrices](/Matrix.md "wikilink") and [Vectors](/Vector.md "wikilink")
-   Significantly improved train synchronization
-   Improved all sound functions to work with player elements

Scripting
---------

### Scripting: New functions

#### Client

-   [createEffect](/createEffect.md "wikilink")
-   [setEffectSpeed](/setEffectSpeed.md "wikilink")
-   [getEffectSpeed](/getEffectSpeed.md "wikilink")
-   [setEffectDensity](/setEffectDensity.md "wikilink")
-   [getEffectDensity](/getEffectDensity.md "wikilink")
-   [getLocalization](/getLocalization.md "wikilink")
-   [isChatVisible](/isChatVisible.md "wikilink")
-   [downloadFile](/downloadFile.md "wikilink")
-   [isTrainChainEngine](/isTrainChainEngine.md "wikilink")

#### Server

-   [isBan](/isBan.md "wikilink")
-   [setBanAdmin](/setBanAdmin.md "wikilink")
-   [setBanReason](/setBanReason.md "wikilink")
-   [setUnbanTime](/setUnbanTime.md "wikilink")
-   [getAccountsBySerial](/getAccountsBySerial.md "wikilink")
-   [getAccountSerial](/getAccountSerial.md "wikilink")

#### Shared (*Client & Server side*)

-   [isElementWaitingForGroundToLoad](/isElementWaitingForGroundToLoad.md "wikilink")
-   Added additional optional parameter bInstant to setPlayerMoney to instantly set the money without counting up/down
-   Fixed toJSON/fromJSON not handling binary data properly

### Scripting: New Events

#### Client

-   [onClientFileDownloadComplete](/onClientFileDownloadComplete.md "wikilink")

#### Server

-   [onWeaponFire](/onWeaponFire.md "wikilink")

### Scripting: Changes, Bugfixes and Additions

-   Fixed getResourceConfig() not working on foreign resources
-   Fixed the Brown Streak Carriage (ID: 570)
-   Changed attachTrailerToVehicle to support trains

Client
------

### Client: Additions

-   Distinguish between left and right Shift, Ctrl and Alt presses.
-   Added SettingHUDMatchAspectRatio, SettingAspectRatio to dxGetStatus.
-   Added support for the use of [Opus Codec](https://en.wikipedia.org/wiki/Opus_codec) audio files in playSound and playSound3D.

### Client: Bugfixes & Changes

-   Fixed the money “counts down” GTA-Style when you change a server.
-   Fixed peds being invulnerable to gun fire when doing a drive by.
-   Fixed onClientPlayerDamage not triggering for spray can.
-   Satchels should now be removed on [resetMapInfo](/resetMapInfo.md "wikilink").
-   Fixed getPedMoveState returns false when moving in crouch state
-   Fixed guiScrollPaneGetVerticalScrollPosition returning strange and stepped values.
-   Fixed setPedCameraRotation not working.
-   Fixed peds continuing to fire their weapons after running out of ammo.
-   Fixed radio titles not always showing.
-   Fixed radio music skipping when browsing between different channels.
-   Fixed user track skip (F5) being disabled.
-   Fixed vehicles falling through the map.

Server
------

### Server: Additions

-   [setElementDimension](/setElementDimension.md "wikilink") should now apply to children
-   More descriptive module error messages
-   Commands: unloadmodule and reloadmodule
-   Added server side custom weapons.

### Server: Bugfixes & Changes

-   Fixed 128 character limit in [setAccountData](/setAccountData.md "wikilink")
-   Wildcard bans should now be checked properly on connect
-   Fixed Team members not being sent to clients if set in [onResourceStart](/onResourceStart.md "wikilink").

Resources
---------

-   None yet

Editor
------

-   None yet

Extra information
-----------------

''More detailed information available on [Bug tracker Changelog](https://bugs.multitheftauto.com/changelog_page.php) and Google Code repositories:

:\* [MTA: SA Blue](https://code.google.com/p/mtasa-blue/source/list)

:\* [MTA: SA Official Resources](https://code.google.com/p/mtasa-resources/source/list)

[pl:Changes\_in\_1.4](/pl:Changes_in_1.4.md "wikilink") [pt-br:Novidades\_na\_versão\_1.4.0](/pt-br:Novidades_na_versão_1.4.0.md "wikilink") [ru:Changes\_in\_1.4.0](/ru:Changes_in_1.4.0.md "wikilink")

[Category:Changelog](/Category:Changelog.md "wikilink") [Category:Changes in 1.4](/Category:Changes_in_1.4.md "wikilink")
