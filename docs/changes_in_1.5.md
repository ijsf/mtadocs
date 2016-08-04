Main Additions / Changes
------------------------

-   Added a built-in web browser into MTA (*CEF*) which can be controlled by scripts using a new [browser](/docs/Element/Browser.md "wikilink") element.
-   Added light functions

Scripting
---------

### Scripting: New functions

#### Client

-   [createBrowser](/docs/createBrowser.md "wikilink")
-   [executeBrowserJavascript](/docs/executeBrowserJavascript.md "wikilink")
-   [focusBrowser](/docs/focusBrowser.md "wikilink")
-   [isBrowserFocused](/docs/isBrowserFocused.md "wikilink")
-   [getBrowserProperty](/docs/getBrowserProperty.md "wikilink")
-   [getBrowserTitle](/docs/getBrowserTitle.md "wikilink")
-   [getBrowserURL](/docs/getBrowserURL.md "wikilink")
-   [injectBrowserMouseDown](/docs/injectBrowserMouseDown.md "wikilink")
-   [injectBrowserMouseMove](/docs/injectBrowserMouseMove.md "wikilink")
-   [injectBrowserMouseUp](/docs/injectBrowserMouseUp.md "wikilink")
-   [injectBrowserMouseWheel](/docs/injectBrowserMouseWheel.md "wikilink")
-   [isBrowserLoading](/docs/isBrowserLoading.md "wikilink")
-   [isBrowserDomainBlocked](/docs/isBrowserDomainBlocked.md "wikilink")
-   [loadBrowserURL](/docs/loadBrowserURL.md "wikilink")
-   [requestBrowserDomains](/docs/requestBrowserDomains.md "wikilink")
-   [setBrowserProperty](/docs/setBrowserProperty.md "wikilink")
-   [setBrowserRenderingPaused](/docs/setBrowserRenderingPaused.md "wikilink")
-   [setBrowserVolume](/docs/setBrowserVolume.md "wikilink")
-   [createLight](/docs/createLight.md "wikilink")
-   [getLightType](/docs/getLightType.md "wikilink")
-   [getLightRadius](/docs/getLightRadius.md "wikilink")
-   [getLightColor](/docs/getLightColor.md "wikilink")
-   [getLightDirection](/docs/getLightDirection.md "wikilink")
-   [setLightRadius](/docs/setLightRadius.md "wikilink")
-   [setLightColor](/docs/setLightColor.md "wikilink")
-   [setLightDirection](/docs/setLightDirection.md "wikilink")
-   [getCameraFieldOfView](/docs/getCameraFieldOfView.md "wikilink")
-   [setCameraFieldOfView](/docs/setCameraFieldOfView.md "wikilink")
-   [getPedOccupiedVehicleSeat](/docs/getPedOccupiedVehicleSeat.md "wikilink")
-   [getCameraShakeLevel](/docs/getCameraShakeLevel.md "wikilink")
-   [setCameraShakeLevel](/docs/setCameraShakeLevel.md "wikilink")

#### Server

-   None yet

#### Shared (*Client & Server side*)

-   None yet

### Scripting: New Events

#### Client

-   [onClientBrowserCreated](/docs/onClientBrowserCreated.md "wikilink")
-   [onClientBrowserDocumentReady](/docs/onClientBrowserDocumentReady.md "wikilink")
-   [onClientBrowserLoadingStart](/docs/onClientBrowserLoadingStart.md "wikilink")
-   [onClientBrowserLoadingFailed](/docs/onClientBrowserLoadingFailed.md "wikilink")
-   [onClientBrowserNavigate](/docs/onClientBrowserNavigate.md "wikilink")
-   [onClientBrowserPopup](/docs/onClientBrowserPopup.md "wikilink")
-   [onClientBrowserCursorChange](/docs/onClientBrowserCursorChange.md "wikilink")
-   [onClientBrowserTooltip](/docs/onClientBrowserTooltip.md "wikilink")
-   [onClientBrowserInputFocusChanged](/docs/onClientBrowserInputFocusChanged.md "wikilink")
-   [onClientBrowserWhistelistChange](/docs/onClientBrowserWhistelistChange.md "wikilink")
-   [onClientPlayerNetworkStatus](/docs/onClientPlayerNetworkStatus.md "wikilink")
-   [onClientBrowserResourceBlocked](/docs/onClientBrowserResourceBlocked.md "wikilink")

#### Server

-   [onPlayerNetworkStatus](/docs/onPlayerNetworkStatus.md "wikilink")

### Scripting: Changes, Bugfixes and Additions

-   Added *throttled* parameter to [playSound](/docs/playSound.md "wikilink") and [playSound3D](/playSound3D.md "wikilink")
-   Added resource meta option <download_priority_group> to allow certain client resources to download and start earlier or later than other resources when a player first connects to a server.
-   Added number of simultaneous render targets capability to [dxGetStatus](/docs/dxGetStatus.md "wikilink").
-   Added an option to [addAccount](/docs/addAccount.md "wikilink") to check for case insensitive name clashes.

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
-   Fixed [getAccountData](/docs/getAccountData.md "wikilink") leaking memory
-   Fixed [removeBan](/docs/removeBan.md "wikilink") crashing the server under certain circumstances
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

[Category:Changelog](/docs/Category:Changelog.md "wikilink") [Category:Incomplete](/Category:Incomplete.md "wikilink")
