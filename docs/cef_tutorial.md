This page gives you a brief introduction to CEF.

What is CEF?
============

CEF stands for **C**hromium **E**mbedded **F**ramework and is a framework for embedding Chromium-based browsers in other applications - in our case MTA. CEF is based on Google's Chromium project so it is also a fast, secure and stable web engine.

You can find more information about CEF on CEF's GoogleCode project page: <https://bitbucket.org/chromiumembedded/cef>

The basics
==========

Creating a new browser is really simple. Let's open YouTube for example:

``` lua
-- Create a new remote browser (size is 800*600px) with transparency enabled
local browser = createBrowser(800, 600, true, true)

-- "Wait" for the browser (this is necessary, because CEF runs in a secondary thread and hence requires the 'asynchronous' event mechanism)
addEventHandler("onClientBrowserCreated", browser,
    function()
        -- We're ready to load the URL now (the source of this event is the browser that has been created)
        loadBrowserURL(source, "https://youtube.com/")
    end
)
```

This example does not require any domain requests as YouTube is whitelisted by default. More about domain requests below.

Domain request system
=====================

In order to prevent people from abusing the possibilities CEF offers, we decided to introduce a request system. This means the domain you want to load has to meet at least one of the following requirements:

-   it is whitelisted globally by the MTA team (you can create a post in \[this topic\] to suggest a new domain to be whitelisted) - **\*\*TODO: Add forum URL here\*\***
-   the domain was requsted via requestBrowserDomains/Browser.requestDomains and accepted by the player **before**
-   the domain is on the user's whitelist (MTA settings =&gt; Tab: Browser =&gt; Whitelist)

Apart from these options a domain might be blacklisted due to malicious content. Such domains cannot be requested.

Local vs remote mode
====================

There are two modes CEF can run in:

Characteristics of local mode:

-   you **can** execute Javascript code without any restriction (See: [executeBrowserJavascript](/docs/executebrowserjavascript.md "wikilink"))
-   you **can** only load websites stored in the resource folder
-   you **cannot** load remote content

Characteristics of remote mode:

-   you **cannot** execute Javascript code
-   you **can** only load remote content
-   keep in mind that either loading remote websites or Javascript on remote websites can be disabled in the MTA settings

Changing the mode after the browser was created is not possible due to technical reasons.

Resource management
===================

How to load local HTML files
----------------------------

Loading local HTML files works similar to loading images.

Add your HTML files to your meta.xml through the file tag:

``` xml
<file src="html/myAwesomeUI.html"/>
```

How to load local resources in local HTML files
-----------------------------------------------

Imagine you want to load an image or play a video from your MTA resource. This is possible via a custom URI scheme named ***mtalocal://***

### Example

This examples shows how to play a video. Note that you have to enable OOP.

#### Lua

``` lua
-- Create a browser (local mode is also required to access local data)
local webView = Browser(640, 480, true, true)

addEventHandler("onClientBrowserCreated", webView,
     function()
    
          -- Load HTML UI
          webView:loadURL("http://mta/local/html/myVideo.html")

     end
)
```

#### meta.xml

``` lua
<file src="html/myVideo.html"/>
<file src="media/myVideo.webm"/>
```

#### HTML

This is the most interesting part:

``` html
<!DOCTYPE HTML>
<html>
<head></head>
<body>
    <video width="640" height="480" controls>
         <source src="http://mta/local/myVideo.webm" type="video/webm"/>
    </video>
</body>
</html>
```

Lua &lt;
========

=&gt; Javascript communication= First of all, communication between Lua and Javascript is only available in local mode due to security reasons.

Lua to Javascript
-----------------

Lua to javascript is pretty easy as you can execute Javascript code from Lua using [executeBrowserJavascript](/docs/executebrowserjavascript.md "wikilink").

So, a bit Lua code around it and you have got the first direction:

-   <https://github.com/Jusonex/mtasa_cef_tools/blob/master/webui/src/WebWindow.lua#L180-189>
-   <https://github.com/Jusonex/mtasa_cef_tools/blob/master/webui/src/mtaevents.js#L9-L15>

Javascript to Lua
-----------------

You are able to trigger a client event via the Javascript method *triggerEvent* which is part of the static class/namespace *mta*. The syntax is as follows:

``` javascript
mta.triggerEvent(string event, var parameter1, var parameter2, var parameter3, ...)
```

The source of this event is always the browser element which triggered the event.

An example is available here:

-   <https://github.com/Jusonex/mtasa_cef_tools/blob/master/webui/examples/html/ui2.html#L66>
-   <https://github.com/Jusonex/mtasa_cef_tools/blob/master/webui/examples/Main.lua#L35-L40>

Debugging
=========

The *web development mode* can be enabled as follows (type it in the client's F8 console):

    start runcode
    crun setDevelopmentMode(true, true)
    debugscript 3

Now, you should be able to see web errors and blocked domains/URLs in the debug window at the bottom.

Things you should keep in mind while working with CEF
=====================================================

You should always keep in mind that some modern browser features are not available on some computers. This is for example true for **WebGL**.

Another problematic feature is **Adobe Flash**. Adobe Flash is enabled by default, but you should avoid using it due to the fact that plugins can be disabled in the settings on the one hand (Java is disabled completely by the way) and Flash is very restrictive on the other hand. Restrictive means it runs in a separate process, uses a very old interface and offers therefore just a few ways to control it. As a consequence you cannot control the volume of flash objects. Fortunately, HTML5 is an even better replacement and provides a very good audio and video interface (http://www.w3schools.com/tags/ref\_av\_dom.asp) which even supports 3D sound (@all bored people among us: Feel free to write a 3D sound 'wrapper' that maps the GTA onto HTML5 coordinates :P).

Advanced usage
==============

Since our CEF implementation does not do z-ordering by default, you have to provide your own z-ordering mechanism. You can find a basic implementation of such a mechanism here: <https://github.com/Jusonex/mtasa_cef_tools> There are also a few utility functions which allow you to integrate these classes easily into your own object-oriented UI system. I'll provide some code to use CEF along with CEGUI soon too.

Performance
===========

Creating lots of browsers does not influence MTA directly (except the fact MTA has to copy the texture data in the main/GTA thread due to technical restrictions), because one part of CEF runs in another process and the other part in a secondary thread. So if you do not want to show the browser, it is definitely the best to destroy the browser. If you cannot destroy the browser (imagine you have to save the website's state for some reason), you can save a lot of resources by disabling rendering via [setBrowserRenderingPaused](/docs/setbrowserrenderingpaused.md "wikilink"). This will stop CEF from rendering new frames/processing input and MTA from copying the texture data.

Troubleshooting
===============

### google.com doesn't work (even though I requested google.com)

Google redirects to a country specific website by default. If you want to prevent Google from doing this, load the following URL: <https://www.google.com/ncr>

Scripting functions
===================

Scripting events
================

[Category:Tutorials](/docs/category-tutorials.md "wikilink")
