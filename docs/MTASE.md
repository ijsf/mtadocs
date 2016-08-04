|                                                                      |
|----------------------------------------------------------------------|
| [Image:MTASElogo\_wiki.png](/Image:MTASElogo_wiki.png.md "wikilink") |

Introduction
------------

MTA Script Editor is a tool for Lua scripters, or an Integrated Development Environment (IDE). What we are aiming for is to speed up process of developing resources. We thought that process of creating new resources and testing them is, let's be honest... a pain in the ass. Even the management of resources can be a bit annoying sometimes. For instance, if you want to add a new script file to your resource first you have to create the file, then add the path to the file into meta.xml. Worst of all, if you ever forget about adding the file to meta.xml you end up hitting your head against the wall wondering why your script doesn't work.

We wanted to do something that would speed this process up so you could do so much in so little time. Previewing resources such as images and sounds have never been so easy. We are aiming for something along the lines of Visual Studio IDE.

What we offer
-------------

We have been working on this tool for quite some time but we had a long break due to lack of time and now I'm the only one working on this because education is more important than “having a nice time”. Even though I'm working alone we are progressing smoothly in the development.

We have implemented the following features:

-   Loading resources
-   Easy resource management
-   Preview resources such as sound and image files
-   Lua and XML syntax highlighting
-   On-the-fly (live) Lua syntax checker
-   'New resource' wizard - allows you to create new resource with a few clicks
-   Switching between resources
-   Tabs for script files
-   C\#'s \#region-like grouping code - useful when working in teams and to keep the code clean
-   Start/stop server and client
-   Join your local server with 1 click
-   Switch between game and Script Editor with only one key on the keyboard
-   ResourceZipper

Screenshots
-----------

-   **Main window** - overall look of the application. On the right you can see a list of MTA functions. You can choose what functions you want to be displayed by changing item in the combo box above it. Are you going to ask what this “silly table” at the bottom of the window is doing? I knew it... It's the syntax checker. As you script the syntax is checked by Lua engine and outputs any errors you've made in the script. It speed up progress because you don't have to go into game and restart the resource to check if you fixed the syntax error. I made a little error on line 1 to show you how it looks:

[Image:MTASEmainwnd.png](/Image:MTASEmainwnd.png.md "wikilink")

-   **New resource wizard** - create a resource with 5 simple steps (3 steps are optional):

[Image:MTASEnewreswizard.png](/Image:MTASEnewreswizard.png.md "wikilink")

-   **Sound player** - preview sounds by double-clicking sound file in the resource explorer:

[Image:MTASEsoundplayer.png](/Image:MTASEsoundplayer.png.md "wikilink")

-   **Image viewer** - preview images by hovering you cursor over nodes in resource explorer:

[Image:MTASEimageviewer.png](/Image:MTASEimageviewer.png.md "wikilink")

-   **Suggested functions** - a “window” similar to the one in Visual Studio showing a list of functions. It also shows a tooltip telling you what the function does and its parameters. It also contains all exported functions from every resource. You can add a 3 new attributes to your exported function tag in meta.xml to let Script Editor display descriptive tooltip, like on the screenshot:
    -   **retval:** return type (eg. bool, marker, int, etc.)
    -   **params:** list of parameters
    -   **description:** short description of the function\[/list\]

[Image:MTSEsuggestedfuncs.png](/Image:MTSEsuggestedfuncs.png.md "wikilink")

  
(screenshot show an example of exported function that in meta.xml looks like the following:)

<code lang="xml"><export function="getBankMarkers" retval="table" params="void" description="Returns a table containing all bank markers." />

</syntaxhighlight>
-   **Function tooltip** (available from 0.3) - tooltip showing function description. Moving mouse over function names in the function list (not the suggested functions list)

[Image:MTASE\_func\_desc.png‎](/Image:MTASE_func_desc.png‎.md "wikilink")

-   **MTA Server Configuration** - a window where you can change server's settings. You won't have to open mtaserver.conf and change the server settings, startup resources, adding modules, etc.

[Image:MTASEserverconfig.png](/Image:MTASEserverconfig.png.md "wikilink")

-   **Customize syntax highlighter** - you can customize many syntax highlighter properties

[Image:MTASEcustomizesyntax.png](/Image:MTASEcustomizesyntax.png.md "wikilink")

-   **Exported functions** - you can view all exported functions from every resource

[Image:MTASEfuncs.png](/Image:MTASEfuncs.png.md "wikilink")

Overview
--------

As you can see we want to simplify resource development and it seems to look pretty nice but we are still in development. There are some good key features that would attract you as a scripter. While we are still in development we wanted to ask you what you think about this tool and what would you like to see included in the release (do not ask when! we do not know when). Any suggestions? You're welcome to suggest some features and if possible we will do our best to implement it. Just visit [our MTA forum topic](http://forum.multitheftauto.com/viewtopic.php?f=91&t=24834) and post your suggestions.

Download
--------

To download the tool, go to [our thread on the MTA forum](http://forum.multitheftauto.com/viewtopic.php?f=91&t=24834). That thread is updated frequently.

Requirements
------------

-   To run this application you need to have .NET 2.0 Framework installed.
-   You should be able to run it on Windows XP and Vista. Works on Windows 7 too!
-   You must have both MTA Client and Server installed.

FAQ
---

### Error/Warning messages at startup

### Loading irrKlang.NET2.0 library failed to load! This means you will not be able to preview sound files.

This message appears most likely for Windows XP/Vista **64bit** users. It may occur on 32bit OS if that machine doesn't have .NET 2.0 SP1 installed.

There is only 1 known way to solve the problem...: Make sure you have .NET 2.0 SP1 installed, if you don't have it you can download it from [Microsoft Download Center](http://www.microsoft.com/Downloads/details.aspx?familyid=79BC3B77-E02C-4AD3-AACF-A7633F706BA5&displaylang=en).

### Error parsing meta.xml

The reason why this window comes up should be explained in the message. It's most likely that your meta.xml has the following XML declarations: <code lang="xml">

<?xml version="1.0" encoding="UTF-8" ?>
<?xml version="1.0" encoding="UTF-16" ?>
</syntaxhighlight>
To solve the problem, simply open the file in WordPad or Notepad (Notepad++ may not solve the problem so use the Windows one), remove that line and save the changes.

.NET 2.0 XML parser doesn't like not “well-formed” XML files, so you may get different messages with different meta.xml files.

**(THIS HAS BEEN FIXED IN 0.3)**

### Not able to save file

If you can't seem to be able to save a file that's probably because you created a new file and the file wasn't added to any resource. This is a bug and will be fixed.

### Problem with horizontal scrollbar

If you have too long line and you paste some code on it, you may get a problem of not being able to scroll to the left (beginning of the line). This is problem with 3rd party library MTA:SE is using. It is not going to be fixed by its author (he's inactive for over 2 years now) and it's hard for us to find what is causing it. In fact, I was also given a link to another nice syntax highlighter library which I may use in the future. I hope this one doesn't have that problem. If you encounter this problem there are a few ways to get to the beginning of the line.

-   start highlighting this line so that caret moves to the left
-   press Home key on your keyboard to move caret to the first character on a line

### Problems with loading some resources (meta.xml)

If you have problems with some resources not being loaded and you get message your resource will not be shown in Resource Explorer, there are few things you can do to fix it: - Make sure your files in not encoded in Unicode (you can open it in Windows' Notepad and save the meta.xml with ANSI encoding, don't use Notepad++ for this task since it may not change file encoding at all). - Make sure you don't have "&" (ampersand) sign anywhere in the file since it may cause meta.xml not being parsed correctly. You should replace ampersands with **&amp;** as this is the correct way to represent an ampersand in XML.

Probably both of these can be fixed by changing/adding little piece of code but unfortunately I wasn't able to figure out what. If you know what can cause this parser error in C\# .NET XML parser than don't hesitate and share this knowledge with me so I can fix this problem.

**(THIS HAS BEEN FIXED IN 0.3)**

Contact
-------

You can find us on [MTA forum](http://forum.multitheftauto.com/viewtopic.php?f=91&t=24834)

Credits
-------

-   [50p](http://forum.mtasa.com/memberlist.php?mode=viewprofile&u=19953) - Programmer & GUI designer.
-   [Fenix1042](http://forum.mtasa.com/memberlist.php?mode=viewprofile&u=30686) - Programmer.
-   [Cazomino05](http://forum.mtasa.com/memberlist.php?mode=viewprofile&u=22437) - XML files with MTA functions and events.
-   MTA Developers - Delivering the amazing GTA:SA Multiplayer MOD that has almost unlimited possibilities...

[es:MTASE](/es:MTASE.md "wikilink")
