Main Additions / Changes
------------------------

-   Added “shared” export type in meta.xml
-   Added Lua source encryption option
-   Added the ability to cancel onClientKey
-   Added escape to onClientKey (can't be cancelled twice in a row)
-   Added SettingHUDMatchAspectRatio, SettingAspectRatio to dxGetStatus

### Client

------------------------------------------------------------------------

#### New Functions

-   Added [playSFX](/docs/playsfx.md "wikilink")
-   Added [playSFX3D](/docs/playsfx3d.md "wikilink")
-   Added [getSFXStatus](/docs/getsfxstatus.md "wikilink")
-   Added [setHeliBladeCollisionsEnabled](/docs/sethelibladecollisionsenabled.md "wikilink")
-   Added [getHeliBladeCollisionsEnabled](/docs/gethelibladecollisionsenabled.md "wikilink")
-   Added [getEventHandlers](/docs/geteventhandlers.md "wikilink")

#### New Events

#### Changes / Bug Fixes

-   Fixed vehicle upgrades
-   Fixed warpPedIntoVehicle causing desync when two players try to enter at the same time via vehicle\_enter and warpPedIntoVehicle
-   Fixed map editor crash
-   Fixed debug filename for compiled scripts
-   Fixed applying weapon mods may remove your weapon
-   Fixed crash when streaming in tec-9 with a replaced weapon model
-   Fixed console(F8) input focus begin lost sometimes
-   Fixed building removal crashing after loading/unloading a model 16 times
-   Fixed projectile-type weapons messing up ammo count
-   Fixed guiCreateFont fails each second time resource is started
-   Fixed client ammo desync when using giveWeapon sometimes
-   Fixed guiLabelGetTextExtent not working with unicode
-   Fixed onColShapeHit isn't triggered for towed vehicles server side
-   Fixed GUI scrollpanes and scrollbars don't trigger onClientMouseEnter/Leave
-   Fixed warpPedIntoVehicle after cancelEvent() of onVehicleStartEnter causes network trouble
-   Fixed onPedWasted not triggered, when ped died because the vehicle he was in, exploded
-   Fixed server createColPolygon
-   Fixed a crash when destroying an object in onClientColShapeHit / onClientElementColShapeHit
-   Fixed lightweight sync packet being misread on the client sometimes
-   Fixed getLatentEventHandles sometimes returning false instead of an empty table
-   Fixed setAccountData clips the digits after the decimal point
-   Fixed peds/players being removed from vehicles that fall through the ground

### Server

------------------------------------------------------------------------

#### New Functions

#### New Events

#### Changes / Bug Fixes

### Resources

-   Added sfxbrowser resource
-   Fixed instant reload exploits for the reload resource
-   Fixed 'Use LODs' option in the map editor resource
-   Fixed various things in admin, acpanel, freeroam, parachute and race resources

### Editor

Extra information
-----------------

''More detailed information available on [Bug tracker Changelog](https://bugs.multitheftauto.com/changelog_page.php) and Google Code repositories:

:\* MTA:SA: from [r5593](https://code.google.com/p/mtasa-blue/source/list?num=25&start=5609) to [r5800](https://code.google.com/p/mtasa-blue/source/list?num=25&start=5800)

:\* Resources: [from r938 to r955](https://code.google.com/p/mtasa-resources/source/list?num=25&start=955)

:\* [MTASA 1.3.4 released](https://forum.mtasa.com/viewtopic.php?f=31&t=64990)

[zh-cn:1.3.4 版本新特性](/docs/zh-cn:1.3.4_版本新特性.md "wikilink")

[Category:Changes in 1.3](/docs/category:changes_in_1.3.md "wikilink") [Category:Incomplete](/Category:Incomplete.md "wikilink")
