Main Additions / Changes
------------------------

-   Added 236 new ped skin ID's which allow servers to apply mods onto them: [Character\_Skins](/docs/Character_Skins.md "wikilink")

Scripting
---------

### Scripting: New functions

#### Client

-   [getTrainTrack](/docs/getTrainTrack.md "wikilink")
-   [isVehicleWindowOpen](/docs/isVehicleWindowOpen.md "wikilink")
-   [setTrainTrack](/docs/setTrainTrack.md "wikilink")
-   [setVehicleWindowOpen](/docs/setVehicleWindowOpen.md "wikilink")

#### Server

-   None yet

#### Shared (*Client & Server side*)

-   [iprint](/docs/iprint.md "wikilink")
-   [print](/docs/print.md "wikilink")
-   [getUserdataType](/docs/getUserdataType.md "wikilink")
-   [inspect](/docs/inspect.md "wikilink")

### Scripting: New Events

#### Client

-   None yet

#### Server

-   None yet

### Scripting: Changes, Bugfixes and Additions

-   Added manuallyChanged parameter to [onPlayerChangeNick](/docs/onPlayerChangeNick.md "wikilink")
-   [setVehiclePlateText](/docs/setVehiclePlateText.md "wikilink") now works with any kind of vehicle, including motorbikes (thanks to **lopezloo**).

Client
------

### Client: Additions

-   Added alternative syntax to [guiGridListAddRow](/docs/guiGridListAddRow.md "wikilink") and [guiGridListInsertRowAfter](/guiGridListInsertRowAfter.md "wikilink")
-   [onClientPlayerDamage](/docs/onClientPlayerDamage.md "wikilink") now supports objects and weapons as attackers.
-   Water elements are now limited to a specific dimension.
-   [onClientVehicleStartEnter](/docs/onClientVehicleStartEnter.md "wikilink") is now cancellable if the local player is entering the vehicle.
-   Added client resource files path info to Advanced tab
-   Added option for [addDebugHook](/docs/addDebugHook.md "wikilink") to skip event/functions.

### Client: Bugfixes & Changes

-   Fixed team members not fully synced until re-set by setPlayerTeam or respawn.

Server
------

### Server: Additions

-   None yet

### Server: Bugfixes & Changes

-   Fixed server crash when using db\* functions during [onDebugMessage](/docs/onDebugMessage.md "wikilink") event.
-   [onElementStopSync](/docs/onElementStopSync.md "wikilink") doesn't triggered when player disconnects.
-   Fixed Fire Extinguisher not triggering [onPedWasted](/docs/onPedWasted.md "wikilink").

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

[Category:Changelog](/docs/Category:Changelog.md "wikilink") [Category:Incomplete](/Category:Incomplete.md "wikilink")
