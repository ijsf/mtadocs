-   Changelog on Mantis: <https://bugs.mtasa.com/changelog_page.php>
-   Full changelog: <https://github.com/multitheftauto/mtasa-blue/commits/1.5.1?page=1>

Main Additions / Changes
------------------------

Scripting
---------

### Client

-   Added [createSearchLight](/docs/createsearchlight.md "wikilink"), [getSearchLightStartPosition](/docs/getsearchlightstartposition.md "wikilink"), [getSearchLightEndPosition](/docs/getsearchlightendposition.md "wikilink"), [getSearchLightStartRadius](/docs/getsearchlightstartradius.md "wikilink"), [getSearchLightEndRadius](/docs/getsearchlightendradius.md "wikilink"), [setSearchLightStartPosition](/docs/setsearchlightstartposition.md "wikilink"), [setSearchLightEndPosition](/docs/setsearchlightendposition.md "wikilink"), [setSearchLightStartRadius](/docs/setsearchlightstartradius.md "wikilink"), [setSearchLightEndRadius](/docs/setsearchlightendradius.md "wikilink")
-   Added [setWindowFlashing](/docs/setwindowflashing.md "wikilink")
-   Fixed position calculation in [dxGetTexturePixels](/docs/dxgettexturepixels.md "wikilink") (thanks to tederis)
-   Added UsingDepthBuffer flag to [dxGetStatus](/docs/dxgetstatus.md "wikilink")

### Server

-   Added [dbPrepareString](/docs/dbpreparestring.md "wikilink")
-   Fixed *Player.outputChat* behaving incorrectly
-   Added [onPlayerACInfo](/docs/onplayeracinfo.md "wikilink") and [resendPlayerACInfo](/docs/resendplayeracinfo.md "wikilink")

### Shared (*Client & Server side*)

-   OOP tweaks and fixes
-   Fixed colon cutting the message printed by assert and error
-   Fixed loadstring and load not accepting UTF-8 strings with BOM
-   Improved error handling for function parameter parsing
-   Changed *coroutine.resume* to output errors by default
-   Added https support for [fetchRemote](/docs/fetchremote.md "wikilink")

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

[Category:Changelog](/docs/category:changelog.md "wikilink")
