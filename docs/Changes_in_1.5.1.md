-   Changelog on Mantis: <https://bugs.mtasa.com/changelog_page.php>
-   Full changelog: <https://github.com/multitheftauto/mtasa-blue/commits/1.5.0?page=1>

Main Additions / Changes
------------------------

-   Fixed shotgun bullet sync
-   Fixed minor Windows 10 compatibility issues
-   Fixed a bunch of crashes
-   Introduced a [new web scheme](/Local_Scheme_Handler.md "wikilink") and deprecated the old mtalocal://
-   Removed dependency on DirectPlay
-   Updated dependencies (e.g. CEF and Google Breakpad)
-   Added a few autofixes
-   Code cleanups
-   Sped up client disconnect
-   Added resumable downloads to auto-updater
-   Fixed text in browsers not being selectable
-   Improved CEF handling in the event of missing files
-   Added file verification for local CEF files
-   Added ability to add more ASE master servers to announce to
-   Fixed warning message when Lua file is 0 bytes
-   Fixed mtasa:// links not working correctly if MTA is already running
-   Fixed team members not being fully synced clientside under certain circumstances
-   Fixed Linux server basic backup missing some files
-   Added option to skip server termination during update
-   Changed requestBrowserDomains to display the cursor while GUI is open
-   Fixed DLL path issues on some computers
-   Fixed loading spinner overlaying itself sometimes
-   Fixed a major memory leak
-   Improved CEF debugging capabilities (see [toggleBrowserDevTools](/toggleBrowserDevTools.md "wikilink"))

Scripting
---------

### Scripting: New functions

#### Client

-   [getBrowserSource](/getBrowserSource.md "wikilink")
-   [getCameraFieldOfView](/getCameraFieldOfView.md "wikilink")
-   [setCameraFieldOfView](/setCameraFieldOfView.md "wikilink")
-   [setBrowserAjaxHandler](/setBrowserAjaxHandler.md "wikilink")
-   [getBrowserVolume](/getBrowserVolume.md "wikilink")
-   [toggleBrowserDevTools](/toggleBrowserDevTools.md "wikilink")

#### Server

-   [fileGetPath](/fileGetPath.md "wikilink")

#### Shared (*Client & Server side*)

### Scripting: New Events

#### Client

-   None yet

#### Server

-   None yet

### Scripting: Changes, Bugfixes and Additions

-   Added *passwordType* for [setAccountPassword](/setAccountPassword.md "wikilink")

Client
------

### Client: Additions

-   None yet

### Client: Bugfixes & Changes

-   Added DDS support to dxCreateTexture

Server
------

### Server: Additions

-   None yet

### Server: Bugfixes & Changes

-   Added callback to [requestBrowserDomains](/requestBrowserDomains.md "wikilink")
-   Fixed a few OOP issues
-   Fixed createMarker triggering onMarkerHit
-   Fixed moving objects being able to move frozen players (thanks to eeew2 for the patch)

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
