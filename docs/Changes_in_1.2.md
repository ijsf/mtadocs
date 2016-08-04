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

-   Added [createSWATRope](/createSWATRope.md "wikilink")
-   Added [toJSON](/toJSON.md "wikilink")
-   Added [fromJSON](/fromJSON.md "wikilink")
-   Added [getDevelopmentMode](/getDevelopmentMode.md "wikilink")
-   Added [setDevelopmentMode](/setDevelopmentMode.md "wikilink")

<!-- -->

-   Added [getVehicleVariant](/getVehicleVariant.md "wikilink")
-   Added [getWeaponProperty](/getWeaponProperty.md "wikilink")
-   Added [getOriginalWeaponProperty](/getOriginalWeaponProperty.md "wikilink")
-   Added [isElementLowLOD‎](/isElementLowLOD‎.md "wikilink")
-   Added [getLowLODElement](/getLowLODElement.md "wikilink")
-   Added [setLowLODElement](/setLowLODElement.md "wikilink")
-   Added [dxSetShaderTessellation](/dxSetShaderTessellation.md "wikilink")

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
-   Added 'showcol' command to see colshapes if [setDevelopmentMode](/setDevelopmentMode.md "wikilink") is set
-   New map image in F11
-   Added opacity keys to radar map and reduced its memory usage
-   Improved bullet accuracy synchronization

Server
------

### New Functions

-   Added [getPlayerIdleTime](/getPlayerIdleTime.md "wikilink")
-   Added [deleteResource](/deleteResource.md "wikilink")
-   Added [renameResource](/renameResource.md "wikilink")
-   Added [dbExec](/dbExec.md "wikilink")
-   Added [dbQuery](/dbQuery.md "wikilink")
-   Added [dbPoll](/dbPoll.md "wikilink")
-   Added [dbConnect](/dbConnect.md "wikilink")
-   Added [dbFree](/dbFree.md "wikilink")
-   Added [getVehicleVariant](/getVehicleVariant.md "wikilink")
-   Added [getWeaponProperty](/getWeaponProperty.md "wikilink")
-   Added [getOriginalWeaponProperty](/getOriginalWeaponProperty.md "wikilink")
-   Added [setVehicleVariant](/setVehicleVariant.md "wikilink")
-   Added [setWeaponProperty](/setWeaponProperty.md "wikilink")
-   Added [resendPlayerModInfo](/resendPlayerModInfo.md "wikilink")
-   Added [isElementLowLOD‎](/isElementLowLOD‎.md "wikilink")
-   Added [getLowLODElement](/getLowLODElement.md "wikilink")
-   Added [setLowLODElement](/setLowLODElement.md "wikilink")
-   Added [getResourceACLRequests](/getResourceACLRequests.md "wikilink")
-   Added [updateResourceACLRequest](/updateResourceACLRequest.md "wikilink")

### New Events

-   Added [onChatMessage](/onChatMessage.md "wikilink")
-   Added [onElementModelChanged](/onElementModelChanged.md "wikilink")

### Changes

-   Major reduction in bandwidth upload usage
-   Updated [createResource](/createResource.md "wikilink") and Fixed [copyResource](/copyResource.md "wikilink")

<!-- -->

-   Added basic backup of some server files
-   Added option to log database queries to a file
-   Added reconnect option to [redirectPlayer](/redirectPlayer.md "wikilink")
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

[Category:Changelog](/Category:Changelog.md "wikilink") [Category:Changes in 1.2](/Category:Changes_in_1.2.md "wikilink")
