Main Additions / Changes
------------------------

-   Added 236 new ped skin ID's which allow servers to apply mods onto them: [Character\_Skins](/docs/character_skins.md "wikilink")

Scripting
---------

### Scripting: New functions

#### Client

-   [getTrainTrack](/docs/gettraintrack.md "wikilink")
-   [isVehicleWindowOpen](/docs/isvehiclewindowopen.md "wikilink")
-   [setTrainTrack](/docs/settraintrack.md "wikilink")
-   [setVehicleWindowOpen](/docs/setvehiclewindowopen.md "wikilink")

#### Server

-   None yet

#### Shared (*Client & Server side*)

-   [iprint](/docs/iprint.md "wikilink")
-   [print](/docs/print.md "wikilink")
-   [getUserdataType](/docs/getuserdatatype.md "wikilink")
-   [inspect](/docs/inspect.md "wikilink")

### Scripting: New Events

#### Client

-   None yet

#### Server

-   None yet

### Scripting: Changes, Bugfixes and Additions

-   Added manuallyChanged parameter to [onPlayerChangeNick](/docs/onplayerchangenick.md "wikilink")
-   [setVehiclePlateText](/docs/setvehicleplatetext.md "wikilink") now works with any kind of vehicle, including motorbikes (thanks to **lopezloo**).

Client
------

### Client: Additions

-   Added alternative syntax to [guiGridListAddRow](/docs/guigridlistaddrow.md "wikilink") and [guiGridListInsertRowAfter](/guiGridListInsertRowAfter.md "wikilink")
-   [onClientPlayerDamage](/docs/onclientplayerdamage.md "wikilink") now supports objects and weapons as attackers.
-   Water elements are now limited to a specific dimension.
-   [onClientVehicleStartEnter](/docs/onclientvehiclestartenter.md "wikilink") is now cancellable if the local player is entering the vehicle.
-   Added client resource files path info to Advanced tab
-   Added option for [addDebugHook](/docs/adddebughook.md "wikilink") to skip event/functions.

### Client: Bugfixes & Changes

-   Fixed team members not fully synced until re-set by setPlayerTeam or respawn.

Server
------

### Server: Additions

-   None yet

### Server: Bugfixes & Changes

-   Fixed server crash when using db\* functions during [onDebugMessage](/docs/ondebugmessage.md "wikilink") event.
-   [onElementStopSync](/docs/onelementstopsync.md "wikilink") doesn't triggered when player disconnects.
-   Fixed Fire Extinguisher not triggering [onPedWasted](/docs/onpedwasted.md "wikilink").

Resources
---------

-   None yet

Editor
------

-   None yet

Extra information
-----------------

''More detailed information available on [Bug tracker Changelog](https://bugs.multitheftauto.com/changelog_page.php) and GitHub repositories:

:\* [MTA: SA Blue](https://github.com/multitheftauto/mtasa-blue)

:\* [MTA: SA Official Resources](https://github.com/multitheftauto/mtasa-resources)

[Category:Changelog](/docs/category:changelog.md "wikilink") [Category:Incomplete](/Category:Incomplete.md "wikilink")
