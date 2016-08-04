Main Additions / Changes
------------------------

-   Added a built-in web browser into MTA (*CEF*) which can be controlled by scripts using a new [browser](/Element/Browser.md "wikilink") element.
-   Added light functions

Scripting
---------

### Scripting: New functions

#### Client

-   [createBrowser](/createBrowser.md "wikilink")
-   [executeBrowserJavascript](/executeBrowserJavascript.md "wikilink")
-   [focusBrowser](/focusBrowser.md "wikilink")
-   [isBrowserFocused](/isBrowserFocused.md "wikilink")
-   [getBrowserProperty](/getBrowserProperty.md "wikilink")
-   [getBrowserTitle](/getBrowserTitle.md "wikilink")
-   [getBrowserURL](/getBrowserURL.md "wikilink")
-   [injectBrowserMouseDown](/injectBrowserMouseDown.md "wikilink")
-   [injectBrowserMouseMove](/injectBrowserMouseMove.md "wikilink")
-   [injectBrowserMouseUp](/injectBrowserMouseUp.md "wikilink")
-   [injectBrowserMouseWheel](/injectBrowserMouseWheel.md "wikilink")
-   [isBrowserLoading](/isBrowserLoading.md "wikilink")
-   [isBrowserDomainBlocked](/isBrowserDomainBlocked.md "wikilink")
-   [loadBrowserURL](/loadBrowserURL.md "wikilink")
-   [requestBrowserDomains](/requestBrowserDomains.md "wikilink")
-   [setBrowserProperty](/setBrowserProperty.md "wikilink")
-   [setBrowserRenderingPaused](/setBrowserRenderingPaused.md "wikilink")
-   [setBrowserVolume](/setBrowserVolume.md "wikilink")
-   [createLight](/createLight.md "wikilink")
-   [getLightType](/getLightType.md "wikilink")
-   [getLightRadius](/getLightRadius.md "wikilink")
-   [getLightColor](/getLightColor.md "wikilink")
-   [getLightDirection](/getLightDirection.md "wikilink")
-   [setLightRadius](/setLightRadius.md "wikilink")
-   [setLightColor](/setLightColor.md "wikilink")
-   [setLightDirection](/setLightDirection.md "wikilink")
-   [getCameraFieldOfView](/getCameraFieldOfView.md "wikilink")
-   [setCameraFieldOfView](/setCameraFieldOfView.md "wikilink")
-   [getPedOccupiedVehicleSeat](/getPedOccupiedVehicleSeat.md "wikilink")
-   [getCameraShakeLevel](/getCameraShakeLevel.md "wikilink")
-   [setCameraShakeLevel](/setCameraShakeLevel.md "wikilink")

#### Server

-   None yet

#### Shared (*Client & Server side*)

-   None yet

### Scripting: New Events

#### Client

-   [onClientBrowserCreated](/onClientBrowserCreated.md "wikilink")
-   [onClientBrowserDocumentReady](/onClientBrowserDocumentReady.md "wikilink")
-   [onClientBrowserLoadingStart](/onClientBrowserLoadingStart.md "wikilink")
-   [onClientBrowserLoadingFailed](/onClientBrowserLoadingFailed.md "wikilink")
-   [onClientBrowserNavigate](/onClientBrowserNavigate.md "wikilink")
-   [onClientBrowserPopup](/onClientBrowserPopup.md "wikilink")
-   [onClientBrowserCursorChange](/onClientBrowserCursorChange.md "wikilink")
-   [onClientBrowserTooltip](/onClientBrowserTooltip.md "wikilink")
-   [onClientBrowserInputFocusChanged](/onClientBrowserInputFocusChanged.md "wikilink")
-   [onClientBrowserWhistelistChange](/onClientBrowserWhistelistChange.md "wikilink")
-   [onClientPlayerNetworkStatus](/onClientPlayerNetworkStatus.md "wikilink")
-   [onClientBrowserResourceBlocked](/onClientBrowserResourceBlocked.md "wikilink")

#### Server

-   [onPlayerNetworkStatus](/onPlayerNetworkStatus.md "wikilink")

### Scripting: Changes, Bugfixes and Additions

-   Added *throttled* parameter to [playSound](/playSound.md "wikilink") and [playSound3D](/playSound3D.md "wikilink")
-   Added resource meta option <download_priority_group> to allow certain client resources to download and start earlier or later than other resources when a player first connects to a server.
-   Added number of simultaneous render targets capability to [dxGetStatus](/dxGetStatus.md "wikilink").
-   Added an option to [addAccount](/addAccount.md "wikilink") to check for case insensitive name clashes.

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
-   Fixed [getAccountData](/getAccountData.md "wikilink") leaking memory
-   Fixed [removeBan](/removeBan.md "wikilink") crashing the server under certain circumstances
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

[Category:Changelog](/Category:Changelog.md "wikilink") [Category:Incomplete](/Category:Incomplete.md "wikilink")
