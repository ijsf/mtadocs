-   Changelog on Mantis: <https://bugs.mtasa.com/changelog_page.php>
-   Full changelog: <https://github.com/multitheftauto/mtasa-blue/commits/1.5.1?page=1>

Main Additions / Changes
------------------------

Scripting
---------

### Client

-   Added [createSearchLight](/createSearchLight.md "wikilink"), [getSearchLightStartPosition](/getSearchLightStartPosition.md "wikilink"), [getSearchLightEndPosition](/getSearchLightEndPosition.md "wikilink"), [getSearchLightStartRadius](/getSearchLightStartRadius.md "wikilink"), [getSearchLightEndRadius](/getSearchLightEndRadius.md "wikilink"), [setSearchLightStartPosition](/setSearchLightStartPosition.md "wikilink"), [setSearchLightEndPosition](/setSearchLightEndPosition.md "wikilink"), [setSearchLightStartRadius](/setSearchLightStartRadius.md "wikilink"), [setSearchLightEndRadius](/setSearchLightEndRadius.md "wikilink")
-   Added [setWindowFlashing](/setWindowFlashing.md "wikilink")
-   Fixed position calculation in [dxGetTexturePixels](/dxGetTexturePixels.md "wikilink") (thanks to tederis)
-   Added UsingDepthBuffer flag to [dxGetStatus](/dxGetStatus.md "wikilink")

### Server

-   Added [dbPrepareString](/dbPrepareString.md "wikilink")
-   Fixed *Player.outputChat* behaving incorrectly
-   Added [onPlayerACInfo](/onPlayerACInfo.md "wikilink") and [resendPlayerACInfo](/resendPlayerACInfo.md "wikilink")

### Shared (*Client & Server side*)

-   OOP tweaks and fixes
-   Fixed colon cutting the message printed by assert and error
-   Fixed loadstring and load not accepting UTF-8 strings with BOM
-   Improved error handling for function parameter parsing
-   Changed *coroutine.resume* to output errors by default
-   Added https support for [fetchRemote](/fetchRemote.md "wikilink")

Client
------

### Client: Additions

-   None yet

### Client: Bugfixes & Changes

-   Updated CEF (and underlying Chromium)
-   Fixed player reconnecting under certain circumstances when downloading a file from an external webserver
-   Fixed door/component desync on vehicle stream-in/out
-   Fixed multiple major crashes
-   Security fixes

Server
------

### Server: Additions

-   Added some Linux libraries to the MTA package to improve compatibility with old systems
-   Added server verification logic

### Server: Bugfixes & Changes

-   Fixed input cursor causing server freezes
-   Fixed refreshResources sometimes crashing the server
-   Fixed file conflicts when a resource name contains square brackets
-   Fixed Linux server startup error message formatting
-   Improved version checks

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

[Category:Changelog](/Category:Changelog.md "wikilink")
