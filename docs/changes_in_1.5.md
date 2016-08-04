Main Additions / Changes
------------------------

-   Added a built-in web browser into MTA (*CEF*) which can be controlled by scripts using a new [browser](/docs/element/browser.md "wikilink") element.
-   Added light functions

Scripting
---------

### Scripting: New functions

#### Client

-   [createBrowser](/docs/createbrowser.md "wikilink")
-   [executeBrowserJavascript](/docs/executebrowserjavascript.md "wikilink")
-   [focusBrowser](/docs/focusbrowser.md "wikilink")
-   [isBrowserFocused](/docs/isbrowserfocused.md "wikilink")
-   [getBrowserProperty](/docs/getbrowserproperty.md "wikilink")
-   [getBrowserTitle](/docs/getbrowsertitle.md "wikilink")
-   [getBrowserURL](/docs/getbrowserurl.md "wikilink")
-   [injectBrowserMouseDown](/docs/injectbrowsermousedown.md "wikilink")
-   [injectBrowserMouseMove](/docs/injectbrowsermousemove.md "wikilink")
-   [injectBrowserMouseUp](/docs/injectbrowsermouseup.md "wikilink")
-   [injectBrowserMouseWheel](/docs/injectbrowsermousewheel.md "wikilink")
-   [isBrowserLoading](/docs/isbrowserloading.md "wikilink")
-   [isBrowserDomainBlocked](/docs/isbrowserdomainblocked.md "wikilink")
-   [loadBrowserURL](/docs/loadbrowserurl.md "wikilink")
-   [requestBrowserDomains](/docs/requestbrowserdomains.md "wikilink")
-   [setBrowserProperty](/docs/setbrowserproperty.md "wikilink")
-   [setBrowserRenderingPaused](/docs/setbrowserrenderingpaused.md "wikilink")
-   [setBrowserVolume](/docs/setbrowservolume.md "wikilink")
-   [createLight](/docs/createlight.md "wikilink")
-   [getLightType](/docs/getlighttype.md "wikilink")
-   [getLightRadius](/docs/getlightradius.md "wikilink")
-   [getLightColor](/docs/getlightcolor.md "wikilink")
-   [getLightDirection](/docs/getlightdirection.md "wikilink")
-   [setLightRadius](/docs/setlightradius.md "wikilink")
-   [setLightColor](/docs/setlightcolor.md "wikilink")
-   [setLightDirection](/docs/setlightdirection.md "wikilink")
-   [getCameraFieldOfView](/docs/getcamerafieldofview.md "wikilink")
-   [setCameraFieldOfView](/docs/setcamerafieldofview.md "wikilink")
-   [getPedOccupiedVehicleSeat](/docs/getpedoccupiedvehicleseat.md "wikilink")
-   [getCameraShakeLevel](/docs/getcamerashakelevel.md "wikilink")
-   [setCameraShakeLevel](/docs/setcamerashakelevel.md "wikilink")

#### Server

-   None yet

#### Shared (*Client & Server side*)

-   None yet

### Scripting: New Events

#### Client

-   [onClientBrowserCreated](/docs/onclientbrowsercreated.md "wikilink")
-   [onClientBrowserDocumentReady](/docs/onclientbrowserdocumentready.md "wikilink")
-   [onClientBrowserLoadingStart](/docs/onclientbrowserloadingstart.md "wikilink")
-   [onClientBrowserLoadingFailed](/docs/onclientbrowserloadingfailed.md "wikilink")
-   [onClientBrowserNavigate](/docs/onclientbrowsernavigate.md "wikilink")
-   [onClientBrowserPopup](/docs/onclientbrowserpopup.md "wikilink")
-   [onClientBrowserCursorChange](/docs/onclientbrowsercursorchange.md "wikilink")
-   [onClientBrowserTooltip](/docs/onclientbrowsertooltip.md "wikilink")
-   [onClientBrowserInputFocusChanged](/docs/onclientbrowserinputfocuschanged.md "wikilink")
-   [onClientBrowserWhistelistChange](/docs/onclientbrowserwhistelistchange.md "wikilink")
-   [onClientPlayerNetworkStatus](/docs/onclientplayernetworkstatus.md "wikilink")
-   [onClientBrowserResourceBlocked](/docs/onclientbrowserresourceblocked.md "wikilink")

#### Server

-   [onPlayerNetworkStatus](/docs/onplayernetworkstatus.md "wikilink")

### Scripting: Changes, Bugfixes and Additions

-   Added *throttled* parameter to [playSound](/docs/playsound.md "wikilink") and [playSound3D](/docs/playsound3d.md "wikilink")
-   Added resource meta option <download_priority_group> to allow certain client resources to download and start earlier or later than other resources when a player first connects to a server.
-   Added number of simultaneous render targets capability to [dxGetStatus](/docs/dxgetstatus.md "wikilink").
-   Added an option to [addAccount](/docs/addaccount.md "wikilink") to check for case insensitive name clashes.

Client
------

### Client: Additions

-   Enabled low fragmentation heap for XP to reduce memory allocation problems.
-   Added automatic TXD resizing for 32 bit OS users to help fix low memory crashes.
-   Added quality argument to dxCreateFont.
-   Added FOV setting in the Video tab.
-   Added support for multiple render targets in shaders.
-   Adds the ability to complete nicknames in the chatbox when the tab key is pressed.
-   Synced server side peds weapons with clients.
-   Added fix for bullet sync not applying damage to the local player during network interruptions by applying remote calculated damage.

### Client: Bugfixes & Changes

-   Moved client log and config files to MTA\\log and MTA\\config
-   Removed BASS error messages for players
-   Tweaked streaming memory size calculation

Server
------

### Server: Additions

-   Added server shutdown disconnect message

### Server: Bugfixes & Changes

-   Set 64 bit modules directory to “x64/modules”
-   Fixed server ignoring module initialization failure
-   Fixed [getAccountData](/docs/getaccountdata.md "wikilink") leaking memory
-   Fixed [removeBan](/docs/removeban.md "wikilink") crashing the server under certain circumstances
-   Fixed HTTP stats being wrong sometimes
-   Fixed sync issues when destroying a vehicle while exitting
-   Added reload to the default start-up list.

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

[Category:Changelog](/docs/category:changelog.md "wikilink") [Category:Incomplete](/docs/category:incomplete.md "wikilink")
