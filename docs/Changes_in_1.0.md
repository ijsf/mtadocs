This page outlines the major and fundamental changes when upgrading from dp2.x to 1.0.

Client
------

### General

-   The settings menu is now much more advanced and allows for more in depth changes, such as the addition of a **Video** tab which allows you to set the resolution

[Image:Settings\_videotab.png](/Image:Settings_videotab.png.md "wikilink")

### Console commands

The console commands now use [CVARS](/Console_Commands_and_CVars.md "wikilink"). This essentially means that the standard commands that are built into MTA now exhibit a different syntax.

Whereas in dp2 you may have done:

`chat_font 2`

In 1.0 you would perform a command that mimics C:

`chat_font = 2`

This applies to all inbuilt commands, except for those that may interface with a server (e.g. *nick* or *me*).

### Chatbox

The chatbox has had minor changes in 1.0. In particular, the text now displays an animation when a new line appears, and the *Page Up* and *Page Down* keys can be used to scroll the chat. Now it is also possible to change the chatbox layout in the settings menu.

[Image:Settings\_chatboxtab.png](/Image:Settings_chatboxtab.png.md "wikilink")

### Host Game

This useful addition allows you to quickly start a game without having to run the MTA Server executable. It is fully functional and based upon the local.conf.

[Image:Hostgame\_window.png](/Image:Hostgame_window.png.md "wikilink")

### Joypad support

From 1.0, users can use their joypad/controller ingame. The keys for your joypad can be configured in the **Binds** tab, and advanced configuration such as analog keys can be configured in the **Controls** tab.

[Image:Settings\_controltab.png](/Image:Settings_controltab.png.md "wikilink")

### Map Editor

The Map Editor is now functional as of 1.0. This is assuming you have the map editor installed. Please see the [Editor manual](/Editor.md "wikilink") for details.

Server
------

The interface of the server is largely the same as dp2.x, there have, however been various tweaks

### Server config

If upgrading from dp2, you should also add any missing variables to your config:

-   **fpslimit**: This sets the FPS limit on your server.
-   **donotbroadcastlan**: This sets whether the server can broadcast to Local Area Network servers

### Commands

The commands of the server console are mostly the same, with the exception of:

-   **refresh** - Previously the refresh command would refresh *all* resources. Now it only detects new resources that are in your resources directory
-   **refreshall** - This new command mimics the previous functioning of refresh, and refreshes all resources - even those which are loaded already.
-   **loadmodule** - Modules can now be loaded using this command without them being set in the server config.

Resources
---------

Many of the default resources have been changed or updated, and new ones have also been added.

-   Resource [realdriveby](http://community.mtasa.com/index.html?p=resources&s=details&id=57) has been added. This will facilitate the driveby mode in vehicles
-   Resource [freeroam](http://community.mtasa.com/index.html?p=resources&s=details&id=43) has been added. (This resource is also needed when you want to run the test mode in the map editor)
-   Resource [parachute](http://code.google.com/p/multitheftauto-resources/source/browse/#svn/trunk/required/parachute) has been added, which facilitates parachutes from single player.
-   Resource [deathmatch](http://multitheftauto-resources.googlecode.com/svn/trunk/optional/deathmatch) has been added. This is a simple frag-/timelimit based deathmatch gamemode with custom map support.
-   Resource [race](http://multitheftauto-resources.googlecode.com/svn/trunk/optional/race/) has undergone many changes and is now much more stable and functional.

Scripting
---------

Much of the scripting interface has changed in 1.0. Almost all resources will need updating in order to function, although the extent of this varies between scripts. All the affected scripting changes can be viewed on [Changes in 1.0](/:Category:Changes_in_1.0.md "wikilink") page.

### Camera functions

The [Camera Functions](/Server_Scripting_Functions#Camera_functions.md "wikilink") have been completely overhauled.

### Player functions

Some [Player functions](/Server_Scripting_Functions#Player_functions.md "wikilink") have been renamed to [Ped functions](/Server_Scripting_Functions#Ped_functions.md "wikilink"). [Category:Changelog](/Category:Changelog.md "wikilink") [Category:Changes in 1.0](/Category:Changes_in_1.0.md "wikilink")
