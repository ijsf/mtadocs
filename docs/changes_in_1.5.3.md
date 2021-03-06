-   Changelog on Mantis: <https://bugs.mtasa.com/changelog_page.php>
-   Full changelog: <https://github.com/multitheftauto/mtasa-blue/commits/1.5.2?page=1>

Main Additions / Changes
------------------------

-   Added duplicate log line filter for script debugging
-   Code cleanups
-   Improved internal error logging
-   Fixed multiple popular crashes
-   Improved streaming of low LOD objects and increased limits
-   Disabled CEF on Windows XP and Vista (Chromium is no longer supported on these platforms)

Scripting
---------

### Client

-   Added [canBrowserNavigateBack](/docs/canbrowsernavigateback.md "wikilink"), [canBrowserNavigateForward](/docs/canbrowsernavigateforward.md "wikilink"), [navigateBrowserBack](/docs/navigatebrowserback.md "wikilink"), [navigateBrowserForward](/docs/navigatebrowserforward.md "wikilink"), [reloadBrowserPage](/docs/reloadbrowserpage.md "wikilink") (thanks to **mabako**!)
-   Added [isBrowserSupported](/docs/isbrowsersupported.md "wikilink")

### Server

-   Added support for multiple statements in [dbQuery](/docs/dbquery.md "wikilink")/[dbExec](/docs/dbexec.md "wikilink")

### Shared (*Client & Server side*)

-   Fixed fileRead crashing when reading more than 10000 bytes
-   Added [fileGetPath](/docs/filegetpath.md "wikilink")
-   Added option for addDebugHook to skip event/functions

Client
------

### Client: Additions

-   Enabled code signing for *CEFLauncher.exe* to improve anti virus software compatibility
-   Added client resource files path info to Advanced tab
-   MTA uses the native resolution by default now

### Client: Bugfixes & Changes

-   Removed VS2008 redistributable from installer as it is no longer required
-   Fixed setBrowserAjaxHandler breaking JSON decoding (thanks to **mabako**)
-   Updated CEF
-   Tweaked optimus detection
-   Added missing model name for model 6458
-   Fixed LOD object issues (see <https://bugs.mtasa.com/view.php?id=9242>)
-   Fixed colshape related crashes (thanks to lopezloo)
-   Tweaked logic of client resource file validation
-   Fixed setBrowserAudio not muting the sound correctly on some websites e.g. YouTube
-   Fixed client incorrectly handling 'no' answer to recommended update question
-   Fixed self-created water becoming invisible sometimes (thanks to **lopezloo**)
-   Made Lua clear loaded files automatically when dereferenced

Server
------

### Server: Additions

-   Added icon for the Windows server
-   Added server logging for redirectPlayer

### Server: Bugfixes & Changes

-   Fixed compatibility issues on older CPU architectures
-   Fixed modules being broken for some revisions
-   Removed warnings for .png files with JPEG contents
-   Changed remaining <min_mta_version> errors to warnings
-   Changed server private IP error to a warning
-   Fixed dbPoll returning early when timeout is used

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

[Category:Changelog](/docs/category-changelog.md "wikilink") [Category:Incomplete](/docs/category-incomplete.md "wikilink")
