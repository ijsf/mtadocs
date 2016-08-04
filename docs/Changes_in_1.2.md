Main Additions
--------------

-   Major bandwidth usage reductions
-   Ability to replace ped models
-   Ability to replace weapon models
-   Threaded database access functions
-   Custom weapon stats
-   Synced and controllable vehicle variants
-   Improved bullet accuracy synchronization

Client
------

### New Functions

-   Added [createSWATRope](/docs/createSWATRope.md "wikilink")
-   Added [toJSON](/docs/toJSON.md "wikilink")
-   Added [fromJSON](/docs/fromJSON.md "wikilink")
-   Added [getDevelopmentMode](/docs/getDevelopmentMode.md "wikilink")
-   Added [setDevelopmentMode](/docs/setDevelopmentMode.md "wikilink")

<!-- -->

-   Added [getVehicleVariant](/docs/getVehicleVariant.md "wikilink")
-   Added [getWeaponProperty](/docs/getWeaponProperty.md "wikilink")
-   Added [getOriginalWeaponProperty](/docs/getOriginalWeaponProperty.md "wikilink")
-   Added [isElementLowLOD‎](/docs/isElementLowLOD‎.md "wikilink")
-   Added [getLowLODElement](/docs/getLowLODElement.md "wikilink")
-   Added [setLowLODElement](/docs/setLowLODElement.md "wikilink")
-   Added [dxSetShaderTessellation](/docs/dxSetShaderTessellation.md "wikilink")

### New Events

-   None yet

### Changes

-   Major reduction in download when playing
-   Ability to replace ped models
-   Ability to replace weapon models
-   Added anisotropic filtering option
-   Added grass toggle option
-   Fixed long vehicles controlled by remote clients sometimes shake weirdly

<!-- -->

-   New client command 'serial' to get ones serial
-   Added 'showcol' command to see colshapes if [setDevelopmentMode](/docs/setDevelopmentMode.md "wikilink") is set
-   New map image in F11
-   Added opacity keys to radar map and reduced its memory usage
-   Improved bullet accuracy synchronization

Server
------

### New Functions

-   Added [getPlayerIdleTime](/docs/getPlayerIdleTime.md "wikilink")
-   Added [deleteResource](/docs/deleteResource.md "wikilink")
-   Added [renameResource](/docs/renameResource.md "wikilink")
-   Added [dbExec](/docs/dbExec.md "wikilink")
-   Added [dbQuery](/docs/dbQuery.md "wikilink")
-   Added [dbPoll](/docs/dbPoll.md "wikilink")
-   Added [dbConnect](/docs/dbConnect.md "wikilink")
-   Added [dbFree](/docs/dbFree.md "wikilink")
-   Added [getVehicleVariant](/docs/getVehicleVariant.md "wikilink")
-   Added [getWeaponProperty](/docs/getWeaponProperty.md "wikilink")
-   Added [getOriginalWeaponProperty](/docs/getOriginalWeaponProperty.md "wikilink")
-   Added [setVehicleVariant](/docs/setVehicleVariant.md "wikilink")
-   Added [setWeaponProperty](/docs/setWeaponProperty.md "wikilink")
-   Added [resendPlayerModInfo](/docs/resendPlayerModInfo.md "wikilink")
-   Added [isElementLowLOD‎](/docs/isElementLowLOD‎.md "wikilink")
-   Added [getLowLODElement](/docs/getLowLODElement.md "wikilink")
-   Added [setLowLODElement](/docs/setLowLODElement.md "wikilink")
-   Added [getResourceACLRequests](/docs/getResourceACLRequests.md "wikilink")
-   Added [updateResourceACLRequest](/docs/updateResourceACLRequest.md "wikilink")

### New Events

-   Added [onChatMessage](/docs/onChatMessage.md "wikilink")
-   Added [onElementModelChanged](/docs/onElementModelChanged.md "wikilink")

### Changes

-   Major reduction in bandwidth upload usage
-   Updated [createResource](/docs/createResource.md "wikilink") and Fixed [copyResource](/copyResource.md "wikilink")

<!-- -->

-   Added basic backup of some server files
-   Added option to log database queries to a file
-   Added reconnect option to [redirectPlayer](/docs/redirectPlayer.md "wikilink")
-   Synchronized vehicle variants
-   Various optimizations and stability improvements
-   Added glitch “highcloserangedamage” to enable/disable extreme close range damage to the glitch functions.
-   Added 'enablesd' server option for competitive gamemodes
-   Various resource optimizations
-   Threaded pure sync to reduce lag in busy servers
-   Upgraded Raknet and sqlite

Resources
---------

-   Scoreboard updated to use dxscoreboard resource
-   Parachute and scoreboard have been optimized
-   Added fastrope resource

Editor
------

-   None yet

[Category:Changelog](/docs/Category:Changelog.md "wikilink") [Category:Changes in 1.2](/Category:Changes_in_1.2.md "wikilink")
