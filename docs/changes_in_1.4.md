Main Additions / Changes
------------------------

-   Localization of MTA's menus
-   [OOP](/docs/oop.md "wikilink") classes
-   [Matrices](/docs/matrix.md "wikilink") and [Vectors](/Vector.md "wikilink")
-   Significantly improved train synchronization
-   Improved all sound functions to work with player elements

Scripting
---------

### Scripting: New functions

#### Client

-   [createEffect](/docs/createeffect.md "wikilink")
-   [setEffectSpeed](/docs/seteffectspeed.md "wikilink")
-   [getEffectSpeed](/docs/geteffectspeed.md "wikilink")
-   [setEffectDensity](/docs/seteffectdensity.md "wikilink")
-   [getEffectDensity](/docs/geteffectdensity.md "wikilink")
-   [getLocalization](/docs/getlocalization.md "wikilink")
-   [isChatVisible](/docs/ischatvisible.md "wikilink")
-   [downloadFile](/docs/downloadfile.md "wikilink")
-   [isTrainChainEngine](/docs/istrainchainengine.md "wikilink")

#### Server

-   [isBan](/docs/isban.md "wikilink")
-   [setBanAdmin](/docs/setbanadmin.md "wikilink")
-   [setBanReason](/docs/setbanreason.md "wikilink")
-   [setUnbanTime](/docs/setunbantime.md "wikilink")
-   [getAccountsBySerial](/docs/getaccountsbyserial.md "wikilink")
-   [getAccountSerial](/docs/getaccountserial.md "wikilink")

#### Shared (*Client & Server side*)

-   [isElementWaitingForGroundToLoad](/docs/iselementwaitingforgroundtoload.md "wikilink")
-   Added additional optional parameter bInstant to setPlayerMoney to instantly set the money without counting up/down
-   Fixed toJSON/fromJSON not handling binary data properly

### Scripting: New Events

#### Client

-   [onClientFileDownloadComplete](/docs/onclientfiledownloadcomplete.md "wikilink")

#### Server

-   [onWeaponFire](/docs/onweaponfire.md "wikilink")

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
-   Satchels should now be removed on [resetMapInfo](/docs/resetmapinfo.md "wikilink").
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

-   [setElementDimension](/docs/setelementdimension.md "wikilink") should now apply to children
-   More descriptive module error messages
-   Commands: unloadmodule and reloadmodule
-   Added server side custom weapons.

### Server: Bugfixes & Changes

-   Fixed 128 character limit in [setAccountData](/docs/setaccountdata.md "wikilink")
-   Wildcard bans should now be checked properly on connect
-   Fixed Team members not being sent to clients if set in [onResourceStart](/docs/onresourcestart.md "wikilink").

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

[pl:Changes\_in\_1.4](/docs/pl:changes_in_1.4.md "wikilink") [pt-br:Novidades\_na\_versão\_1.4.0](/pt-br:Novidades_na_versão_1.4.0.md "wikilink") [ru:Changes\_in\_1.4.0](/ru:Changes_in_1.4.0.md "wikilink")

[Category:Changelog](/docs/category:changelog.md "wikilink") [Category:Changes in 1.4](/Category:Changes_in_1.4.md "wikilink")
