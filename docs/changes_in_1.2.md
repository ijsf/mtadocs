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

-   Added [createSWATRope](/docs/createswatrope.md "wikilink")
-   Added [toJSON](/docs/tojson.md "wikilink")
-   Added [fromJSON](/docs/fromjson.md "wikilink")
-   Added [getDevelopmentMode](/docs/getdevelopmentmode.md "wikilink")
-   Added [setDevelopmentMode](/docs/setdevelopmentmode.md "wikilink")

<!-- -->

-   Added [getVehicleVariant](/docs/getvehiclevariant.md "wikilink")
-   Added [getWeaponProperty](/docs/getweaponproperty.md "wikilink")
-   Added [getOriginalWeaponProperty](/docs/getoriginalweaponproperty.md "wikilink")
-   Added [isElementLowLOD‎](/docs/iselementlowlod‎.md "wikilink")
-   Added [getLowLODElement](/docs/getlowlodelement.md "wikilink")
-   Added [setLowLODElement](/docs/setlowlodelement.md "wikilink")
-   Added [dxSetShaderTessellation](/docs/dxsetshadertessellation.md "wikilink")

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
-   Added 'showcol' command to see colshapes if [setDevelopmentMode](/docs/setdevelopmentmode.md "wikilink") is set
-   New map image in F11
-   Added opacity keys to radar map and reduced its memory usage
-   Improved bullet accuracy synchronization

Server
------

### New Functions

-   Added [getPlayerIdleTime](/docs/getplayeridletime.md "wikilink")
-   Added [deleteResource](/docs/deleteresource.md "wikilink")
-   Added [renameResource](/docs/renameresource.md "wikilink")
-   Added [dbExec](/docs/dbexec.md "wikilink")
-   Added [dbQuery](/docs/dbquery.md "wikilink")
-   Added [dbPoll](/docs/dbpoll.md "wikilink")
-   Added [dbConnect](/docs/dbconnect.md "wikilink")
-   Added [dbFree](/docs/dbfree.md "wikilink")
-   Added [getVehicleVariant](/docs/getvehiclevariant.md "wikilink")
-   Added [getWeaponProperty](/docs/getweaponproperty.md "wikilink")
-   Added [getOriginalWeaponProperty](/docs/getoriginalweaponproperty.md "wikilink")
-   Added [setVehicleVariant](/docs/setvehiclevariant.md "wikilink")
-   Added [setWeaponProperty](/docs/setweaponproperty.md "wikilink")
-   Added [resendPlayerModInfo](/docs/resendplayermodinfo.md "wikilink")
-   Added [isElementLowLOD‎](/docs/iselementlowlod‎.md "wikilink")
-   Added [getLowLODElement](/docs/getlowlodelement.md "wikilink")
-   Added [setLowLODElement](/docs/setlowlodelement.md "wikilink")
-   Added [getResourceACLRequests](/docs/getresourceaclrequests.md "wikilink")
-   Added [updateResourceACLRequest](/docs/updateresourceaclrequest.md "wikilink")

### New Events

-   Added [onChatMessage](/docs/onchatmessage.md "wikilink")
-   Added [onElementModelChanged](/docs/onelementmodelchanged.md "wikilink")

### Changes

-   Major reduction in bandwidth upload usage
-   Updated [createResource](/docs/createresource.md "wikilink") and Fixed [copyResource](/copyResource.md "wikilink")

<!-- -->

-   Added basic backup of some server files
-   Added option to log database queries to a file
-   Added reconnect option to [redirectPlayer](/docs/redirectplayer.md "wikilink")
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

[Category:Changelog](/docs/category:changelog.md "wikilink") [Category:Changes in 1.2](/Category:Changes_in_1.2.md "wikilink")
