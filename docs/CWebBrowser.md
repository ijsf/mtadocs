Potential issues with implementation of CEF (Chromium Embedded Framework)
=========================================================================

This page discusses the issues when implementing an in-game web browser. Some of these need to be resolved before it's safe to include in MTA. The full discussion is here: <http://pastebin.com/m5sqTRqH>

Awesomium vs CEF
----------------

| Awesomium                                                | CEF                                                                                                                                                                  |
|----------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Proven library for embedding web browsers into games** | Also established (mostly in **windowed** applications)                                                                                                               |
| Closed source                                            | **Open source**                                                                                                                                                      |
| <s>Frequent</s> Infrequent updates                       | <span style="color:red;">**Frequent updates**</span>                                                                                                                 |
| Well implemented multi-process design                    | <s>Due to a bad implementation we are probably forced to run CEF in the main process (gta\_sa.exe)</s> Since a few months also well implemented multi-process design |
| Less CPU usage                                           | A bit higher CPU usage, but better multi-threading                                                                                                                   |
| **Small DLLs and static libraries (~19MB extra size)**   | Larger DLLs and static libraries                                                                                                                                     |
| Less features                                            | **More features**                                                                                                                                                    |

Verdict: Go with CEF. We can link the source tree, and push updates frequently as needed. This may prove vital with critical security updates. It'll just require Jusonex to do small 2-600hour changes.

-   I'm not sure if we should really go with CEF since we are probably forced to run CEF in the main process @ “Problems with CEF” --[Jusonex](/docs/User:Jusonex.md "wikilink") 12:24, 5 May 2014 (UTC)

Verdict 2: Go with Awesomium since CEF doesn't match our requirements (as described below).

Verdict 3:

-   I fear that Awesomium updates are and will be very infrequent. Since this is very bad in terms of security, we should ponder on moving back to CEF. CEF also introduced a separate executeable-mode (https://code.google.com/p/chromiumembedded/wiki/GeneralUsage\#Separate\_Sub-Process\_Executable) which might solve the problem stated below. --[Jusonex](/docs/User:Jusonex.md "wikilink") 11:39, 19 August 2014 (CET)

<s>Problems with CEF</s>
------------------------

<span style='color: red;'>**Problems were solved in a newer CEF revision**</span>

<s>CEF implements Chromium's multi-process architecture by “cloning” the application's main process and running *CefExecuteProcess* which blocks the process while executing all the stuff (i.e. audio, rendering etc.). The behaviour leads to **big issues** in case of gta\_sa.exe: *CefExecuteProcess* has to be called from *WinMain*. Since we can't inject a DLL at this time easily, we have to patch GTA either in memory or on the harddisk (which is too crap). As an alternative, CEF provides a setting in order to run it in single-process mode. However this is a bad solution for two reason:

-   Performance and stability (We can't use more than 2GB memory without the LargeAddressAware flag; if GTA uses up to 1GB and CEF as well, we'll run into trouble). Additionally, we can't react to crashes properly
-   Quotation from CEF's developer (- *yeah, CEF's team consists of only 1 developer*): “Single process mode is intended as a development/debugging tool and is not recommended for production use. There are many potential bugs and stability issues related to use of single process mode. You should strongly consider making your application work in multi process mode.” (Source: [1](http://magpcss.org/ceforum/viewtopic.php?f=6&t=3427#p6950))</s>

Flash
-----

-   Not everyone has flash, and there's likely to be great demand for streaming video. HTML5 doesn't cut it at the moment.
-   For it to function, the special “Other Browsers” version of Flash Player needs to be installed from Adobe's Website
    -   Should a suggestion of installation of “Flash for other browsers” be included in the MTA installer?
        -   I think that we shouldn't be prematurely suggesting/promoting/forcing the install of 3rd party software without knowing the exact demand for it. Server owners might find ways around this problem, and we might end up looking like fools for spyware-like adverts (extreme case scenario :P) --[Talidan](/docs/User:Talidan.md "wikilink") 18:32, 17 April 2014 (UTC)
    -   Using user-agent to spoof various HTML5 Browsers may allow dodging of the use of flash. This requires a few things:
        -   A scripting function to set the user agent of the session
        -   Some sample scripts, or some nagging to make sure the community uses HTML5 wherever possible, by the use of user agent or otherwise. We should try and make server owners responsible to avoid taking the lazy route (flash streaming)
-   Note: <http://www.permadi.com/tutorial/flashjscommand/> (limited way of communication) - thanks to [Cazomino05](/docs/User:Cazomino05.md "wikilink")

HTTP Auth
---------

-   Browsers normally have a built-in dialog for logging into an HTTP auth'd website
-   Do we provide the GUI internally or pass an event for script owners to callback on?
    -   I say do this internally. It's somewhat a security thing, i dont think scripts can be trusted necessarilly. --[Talidan](/docs/User:Talidan.md "wikilink") 18:38, 17 April 2014 (UTC)
-   Can we pass ACL auth from the server to website, if they're hosted on the same box?
    -   It's quite niche. See if the use case opens up. --[Talidan](/docs/User:Talidan.md "wikilink") 18:38, 17 April 2014 (UTC)

Pop-ups/New windows
-------------------

-   How to handle?
    -   Fire an event. This means an event is fired when a web page requests a pop-up or a href in a new window, and it's left for the scripter to deal with it. --[Woovie](/docs/User:Woovie.md "wikilink") 18:38, 17 April 2014 (UTC)

Alerts
------

-   How to handle Alert message boxes?
    -   Either we create a message box GUI in CEGUI to fulfil this
    -   Otherwise, we ignore alerts and make them incompatible. This might end up being the better solution.

Other plugins
-------------

-   Are they supported? If so, which ones?
    -   I'm gonna say we disable most plugins, and have a whitelist for approved ones, if feasible. Who want's to deal with crap like Java? --[Talidan](/docs/User:Talidan.md "wikilink") 18:32, 17 April 2014 (UTC)
    -   If we disable most we need a function to get the list of installed plugins for scripters so they can detect this --[Cazomino05](/docs/User:Cazomino05.md "wikilink") 18:49, 17 April 2014 (UTC)

Whitelist/Blacklist of websites
-------------------------------

-   Global blacklist?
-   How to implement whitelist popup?

Current proposal consists of:

-   A global whitelist of approved websites, that are always allowed. E.g. youtube, google, reddit
-   All other websites have a message box popup requesting that you allow access to certain websites
-   A possible global blacklist/killswitch for bad websites or the entire web browser.

Audio & 3D
----------

-   Audio support in Chromium/Awesomium/CEF is currently multi-threaded. This means it can't be integrated with BASS, which would have opened up possibilities for all the nice BASS functions we have.
-   This also means 3D support can't be added as easily. We can however adjust the volume manually, like we do currently.
    -   Unfortunately, Chromium uses COM volume control. This means that it uses Windows global settings, and for XP/2000 probably can't be controlled easily. 3D might not be possible for these systems.
        -   HTML5 does support volume control. So long as the audio source is on an HTML5 page, these can be wrapped locally with a crafted .html document. This can be fed with volume controls to simulate 3D in Lua, rather than in MTA itself.

Privacy and cookies
-------------------

-   Cookies should not be transferred from one server to another. If you login to Google on one server, another server should not be able to hijack that session.
    -   Easy solution: Delete cookie and cache data upon quit every single time (or perhaps on start in case of crashes?)
    -   Otherwise, CEF offers a Cookie Manager where cookie sessions can be created. Each server could have it's own cookie session so it could remember logins etc, which could be handy for login panels
        -   If this option is chosen, we should have a button in the settings menu to clear all browsing data.

Ability to modify content
-------------------------

-   The ability to modify content inside the web page is quite a useful one however it leaves us prone to javascript attacks such as the ones used in XSS.
    -   Solution: For a first release it would be best that content inside the browser be uneditable as this could lead to security issues. --[Cazomino05](/docs/User:Cazomino05.md "wikilink") 18:49, 17 April 2014 (UTC)

Ability to view content in Screen shots
---------------------------------------

-   Sensitive information can be leaked in script taken screen shots
    -   Solution: As with our current implementation of the chat box the web browsers should be hidden from takePlayerScreenShot as these can be sent to server owners/admins and reveal sensitive information. --[Cazomino05](/docs/User:Cazomino05.md "wikilink") 18:49, 17 April 2014 (UTC)

Authentification
----------------

-   Sensitive key presses can be intercepted via script
    -   Solution: Educate - Window on entry explaining the insecurities of putting personal details into a website and a reminder in edit boxes --[Cazomino05](/docs/User:Cazomino05.md "wikilink") 00:21, 23 April 2014 (UTC)
        -   reminder should be a string in all edit fields depending on if it's remote or local saying something like Insecure to remind people not to put those details in. --[Cazomino05](/docs/User:Cazomino05.md "wikilink") 00:21, 23 April 2014 (UTC)

Prevent subsequent loading of HTML code via javascript
------------------------------------------------------

Since we need javascript to create HTML GUIs, it'd be bad to disable javascript (for local HTML pages) entirely.

-   Problem: A function like *executeBrowserJavascript* would allow loading HTML code via *document.write*.
    -   Possible solution: Don't implement *executeBrowserJavascript* and introduce a “web” flag in the *meta.xml* file. If this flag is set, *fileOpen* will only work in read-only mode. (You'll have to set the web flag then in order to be able to open the website via *loadBrowserURL*).

Negative: Less possibilities --[Jusonex](/docs/User:Jusonex.md "wikilink") 11:16, 09 May 2014 (UTC)
