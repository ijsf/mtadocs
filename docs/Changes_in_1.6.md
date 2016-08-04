Main Additions / Changes
------------------------

-   Added 236 new ped skin ID's which allow servers to apply mods onto them: [Character\_Skins](/Character_Skins.md "wikilink")

Scripting
---------

### Scripting: New functions

#### Client

-   [getTrainTrack](/getTrainTrack.md "wikilink")
-   [isVehicleWindowOpen](/isVehicleWindowOpen.md "wikilink")
-   [setTrainTrack](/setTrainTrack.md "wikilink")
-   [setVehicleWindowOpen](/setVehicleWindowOpen.md "wikilink")

#### Server

-   None yet

#### Shared (*Client & Server side*)

-   [iprint](/iprint.md "wikilink")
-   [print](/print.md "wikilink")
-   [getUserdataType](/getUserdataType.md "wikilink")
-   [inspect](/inspect.md "wikilink")

### Scripting: New Events

#### Client

-   None yet

#### Server

-   None yet

### Scripting: Changes, Bugfixes and Additions

-   Added manuallyChanged parameter to [onPlayerChangeNick](/onPlayerChangeNick.md "wikilink")
-   [setVehiclePlateText](/setVehiclePlateText.md "wikilink") now works with any kind of vehicle, including motorbikes (thanks to **lopezloo**).

Client
------

### Client: Additions

-   Added alternative syntax to [guiGridListAddRow](/guiGridListAddRow.md "wikilink") and [guiGridListInsertRowAfter](/guiGridListInsertRowAfter.md "wikilink")
-   [onClientPlayerDamage](/onClientPlayerDamage.md "wikilink") now supports objects and weapons as attackers.
-   Water elements are now limited to a specific dimension.
-   [onClientVehicleStartEnter](/onClientVehicleStartEnter.md "wikilink") is now cancellable if the local player is entering the vehicle.
-   Added client resource files path info to Advanced tab
-   Added option for [addDebugHook](/addDebugHook.md "wikilink") to skip event/functions.

### Client: Bugfixes & Changes

-   Fixed team members not fully synced until re-set by setPlayerTeam or respawn.

Server
------

### Server: Additions

-   None yet

### Server: Bugfixes & Changes

-   Fixed server crash when using db\* functions during [onDebugMessage](/onDebugMessage.md "wikilink") event.
-   [onElementStopSync](/onElementStopSync.md "wikilink") doesn't triggered when player disconnects.
-   Fixed Fire Extinguisher not triggering [onPedWasted](/onPedWasted.md "wikilink").

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

[Category:Changelog](/Category:Changelog.md "wikilink") [Category:Incomplete](/Category:Incomplete.md "wikilink")
