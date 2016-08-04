[thumb|Proof of concept.](/docs/File:Am3.jpg.md "wikilink") Multi Theft Auto (MTA) is the world's first multiplayer add-on for the Grand Theft Auto 3 Trilogy[1]. Starting as a very simple two player system with no on-foot support, has become one of the most active (multiplayer) add-ons for Grand Theft Auto.

Although often referred to as a modification, Multi Theft Auto is based on [code injection](http://en.wikipedia.org/wiki/Code_injection) and [hooking](http://en.wikipedia.org/wiki/Hooking) techniques whereby the game is manipulated without altering any original files supplied with the game. The software functions as a [game engine](http://en.wikipedia.org/wiki/Game_engine) that installs itself as an extension of the original game, adding core functionality such as [networking](http://en.wikipedia.org/wiki/Computer_networking) and [GUI rendering](http://en.wikipedia.org/wiki/Graphical_User_Interface) while exposing the original game's engine functionality through a [scripting language](http://en.wikipedia.org/wiki/Scripting_Language).

Before Multi Theft Auto
-----------------------

[thumb|GTA3:Alternative Multiplayer](/docs/File:Gta3am01.jpg.md "wikilink") In February 2003, IJs (formerly known as IJsVogel), founder of the project, was searching for a trainer for GTA3. He stumbled upon the GTA3 Admin Console[2] and its source code. When looking through the code he found a way to read all the data from the previous used car, and he decided to synchronize this with two computers over a network. The result of this was the creation of GTA3:AM, less than an hour later.

However, after the release it was difficult to convince people it actually worked because of various hoaxes and earlier attempts that had failed. This was the start of the MTA project.

History of Multi Theft Auto
---------------------------

### Milestones 2003-2006

Main article: [Timeline](/docs/Timeline.md "wikilink")

### Milestones since 2006

[thumb|MTA:SA 1.0 Main Menu](/docs/File:MTA_Main_Menu_1.0.x.png.md "wikilink")

-   **January 3, 2008 MTA:San Andreas 1.0 Deathmatch Developer Preview(s)**

MTA:San Andreas Deathmatch Developer Preview 1 was the first release that featured on-foot synchronization for San Andreas. The name deathmatch refers to the ability to shoot with weapons and get on-foot unlike the race version. The tag deathmatch has been dropped in later releases because this version allowed customized gamemodes with LUA scripting and confused people. While the first 5 releases were called 'Developer Preview' it was very popular.

-   **August 21, 2009 MTA:San Andreas 1.0 released**

Version 1.0.x was released with the GPLv3 license this allowed to work with more people on the next release when it became open source.

-   **August 25, 2011 MTA:San Andreas 1.1 released**
    -   Custom vehicle handling
    -   Voice chat
    -   Improved sound support, including streaming audio (BASS library[3])
    -   Custom shaders
-   **December 17, 2011 MTA:San Andreas 1.2 released**
    -   Custom weapon stats
    -   Ability to replace weapon models
    -   Ability to replace ped models
    -   Major bandwidth usage reductions
-   **2011 Mod of the Year - Players Choice \#1**[4]
-   **January 24, 2012 MTA:San Andreas 1.3 released**
    -   Fixes for various network problems which occured in 1.1 and 1.2 series. (including a fix for “Map download breaking often on large transfers” issue)
    -   Added new scripting functions for removal of default GTASA map objects. (including breakable ones)
    -   Introduced a new scripting event. - [onClientVehicleCollision](/docs/onClientVehicleCollision.md "wikilink")
    -   Implemented a new scripting function. - [takePlayerScreenShot](/docs/takePlayerScreenShot.md "wikilink")
    -   Fixes for various crashes and issues. (including “warp glitch”, inaccurate heat seekers sync, createProjectile() velocity desync between clients, custom models texture crash, “white models” when using custom models and more)
    -   Added functionality to protect client-side scripts which pre-compiles them before being sent and stops resources from being saved on disk. This is configurable in the resource's meta.xml.
    -   Added pixel manipulation functionality.
    -   Introduced new client-side scripting functions - [setBirdsEnabled](/docs/setBirdsEnabled.md "wikilink") and [getBirdsEnabled](/getBirdsEnabled.md "wikilink")
    -   Included a new gui skin - [Lighter black](http://forum.mtasa.com/viewtopic.php?f=139&t=36010#p371815) - contributed by Aibo
-   **September 3, 2012 MTA:San Andreas 1.3.1 released**
    -   Added support for Windows 8
    -   MTA:SA client installers (main and nightlies) are now digitally signed
    -   Increased max players for a single server to 4096
    -   New features: BASS Effects ([video](http://www.youtube.com/watch?v=3sMlgF9LKPs)), Analog Controls States, Bullet Sync and Custom Vehicle Sirens ([video1](http://www.youtube.com/watch?v=ZJDrVf3qSm0) [video2](http://www.youtube.com/watch?v=1J0_v85FioA) [video3](http://www.youtube.com/watch?v=X3zE6hZOx4c))
    -   Added ability to create pedless weapons via weapon creation ([video](http://www.youtube.com/watch?v=LN1nZZnzlms))
    -   Added ability to shoot with any weapon with jetpack ([video1](http://www.youtube.com/watch?v=mFQOyyLfo5U) [video2](http://www.youtube.com/watch?v=_JuQqQ8g67A))
    -   Editor stability improvements and new features
-   **November 4, 2012 Over ten thousand concurrent players online**

On that day, at 17.30 UTC we had over ten thousand concurrent players online on all MTASA servers around the world. That was more than the number of players combined playing GTA4 and EFLC on Steam at the time, or other hit titles such as Call of Duty: Black Ops or Total War: Shogun 2 (according to [Steam Stats](http://store.steampowered.com/stats/)). This shows, that after all these years there is still a lot of interest in the older GTA games, especially the will to play them online with friends. This also shows that you guys appreciate what we do, and that makes us very happy! The current record is 11128 concurrent players, set on 22nd December, so there is still room to improve.[5]

-   **May 5, 2013 MTA:San Andreas 1.3.2 released**
    -   Client setting: Turn off selected sounds when minimized.
    -   Client setting: Added aim vertical sensitivity setting.
    -   Client setting: Added process priority setting.
    -   Added glitch 'hitanim' to allow 'being hit by bullet' animation when aiming certain weapons.
    -   Added 'sinfo' command to client to output server info.
    -   Added 'showframegraph' command for displaying frame timings.
    -   Added server multiple IP support.
    -   Reduced stutter on big maps.
    -   Fixed vehicles losing velocity on race respawn .
    -   Fixed a server browser crash.
    -   Fixed smoothness when using server setting 'latency\_reduction'.
    -   Fixed PNG files with alpha channel sometimes being all black.
    -   Fixed a cause of train desync.
    -   Fixed depth buffer shaders not working right with mirrors.
-   **July 2, 2013 MTA:San Andreas 1.3.3 released**
    -   Anti-cheat updates.
    -   Optimized streamer to work better with complex maps.
    -   Smoothed fonts when scaling chat box.
    -   Added option to scale HUD elements correctly for widescreen.
    -   Added option to disable OS and graphic driver 'tweaks', as they can interfere with MTA.
    -   Better compatibility with NVidia Optimus laptops.
    -   Improved server performance.
    -   Updated our Audio Library to the latest version to improve some of our sound functions specifically beat detection and prevent crashes caused by calling getSoundMetaTags.
-   **September 7, 2013 MTA:San Andreas 1.3.4 released**
    -   Added “shared” export type in meta.xml
    -   Added Lua source encryption option
    -   Added the ability to cancel onClientKey
    -   Added escape to onClientKey (can't be cancelled twice in a row)
    -   Added SettingHUDMatchAspectRatio, SettingAspectRatio to dxGetStatus

Versions
--------

### [GTA3:MTA](/docs/Archive#Multi_Theft_Auto_0.5.md "wikilink")

GTA3:MTA was originally named GTA3:AM (Alternative Multiplayer) But since there was no other multiplayer available this could hardly be an alternative. It started out as a two player system with the so-called previous-car-method. Before going to MTA:VC there were 3 versions released. 0.1a and 0.2a only supported the previous-car-method, whilst 0.3b was more advanced and had a lot more synchronization. These original versions were written in Visual Basic. The 0.3b server however was made in C++ and was available for Win32 and Linux.

The GTA3:MTA series was discontinued until the latter half of 2004 when it was picked up again with MTA 0.4. Support for GTA3 was later improved in version 0.5.

It has been said many times that GTA3:MTA was based on code left behind by Rockstar, the developers of GTA3. Even though there is left-over multiplayer content in GTA3, none of the code left behind was used for MTA.

### [MTA:VC](/docs/Archive#Multi_Theft_Auto_0.5.md "wikilink")

When Vice City was released it didn't take long before the MTA project switched to this new game. GTA3 was dropped for the moment and development focused on Vice City. We also took this opportunity to start our codebase from scratch, this time completely in C++. It wasn't until version 0.2 that we could see major improvements. 0.2 was the first version to feature a new chat box system and score board. Later versions of MTA:VC had mixed results. Some people still prefer the gameplay from 0.2.2 or 0.3. Some call the latest version (0.5) a failure. In February 2005 MTA 0.5.1 preview was shown to the public, addressing known issues and adding new features.[6] 0.5.1 was never released.

### '[Blue](/docs/Blue.md "wikilink")'

In late 2003 a spin-off project was launched codenamed Blue. The goal of this project was to try out new ideas and then backport them to the current codebase. Due to the “ugly” coding of the MTA:VC codebase it was decided that there would be no backporting and that the Blue codebase would form the basis of a new MTA project that, when finished, would be easy to adapt to new games. Initially set for Vice City, the development didn't pick up pace until San Andreas was released in June 2005. MTA:SA is built upon the Blue project. The concepts used in this project also make it possible for user add-ons to be added to the game, and therefore a decision was made to not simply create a multiplayer mod, but rather a multiplayer-enabled Software Development Kit (SDK).

### [MTA:SA Race](/docs/Archive#MTA:_San_Andreas_Race.md "wikilink")

The first release of MTA:SA incorporates only vehicle synchronisation. The team has decided to start once more from scratch and build a modular codebase. Another decision made was to focus on one area of the game at a time and release when that area is completed. Therefore the first release will only feature gameplay in cars. Also a basic map editor has been added. Even though there is no on-foot sync like with GTA3:AM, there is no comparison between them on a technical basis.

### [MTA:SA (Deathmatch)](/docs/Main_Page.md "wikilink")

Multi Theft Auto's latest release is for the game Grand Theft Auto: San Andreas and is built upon a now open source game engine that has been in development for several years and is the only project that is still actively maintained. The engine provides users with all the necessary tools they need to create their own [game modes](http://en.wikipedia.org/wiki/Gameplay) and [maps](http://en.wikipedia.org/wiki/Level_(video_gaming)) by exposing a large part of the original game functionality through a [Lua scripting machine](http://en.wikipedia.org/wiki/Lua_(programming_language)).

On Saturday, 22nd of August, 2009, Multi Theft Auto: San Andreas v1.0 was officially distributed as the first open source release. This release abandoned the now obsolete “Deathmatch” tag in the product name to emphasize on the versatility of the software. Gameplay functionality is solely provided by the scripting language, so users can choose or develop their own combination of scripts and other contents to customize and host their own type of game.

|                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <div align="center">                                                                                                                                                                                                                                                                                                                                                                                                                                            
 <File:SSV> Scramble.png|MTA 0.5 Mini mission on GTA3's Shoreside Vale <File:Vc0.1-3.jpg%7CMTA:VC> 0.1 <File:Mtavcbluelaunching.png%7CMTA> 'Blue' Loading screen <File:MTASA-Race-Mainmenu.png%7CThe> 'Blue' look/interface in MTA:SA Race <File:MTASA-Race-Racing.jpg%7CRacing> in MTA: SA Race <File:Sa-airrace.jpg%7CA> mid-air race in MTA:SA Race <File:Mtasa-nyan.png%7CNyan> Cat in MTA:SA <File:Mta-screen> 2010-09-25 21-59-07.png|Custom map in MTA:SA  
                                                                                                                                                                                                                                                                                                                                                                                                                                                                  
 </div>                                                                                                                                                                                                                                                                                                                                                                                                                                                           |

See Also
--------

-   [Timeline](/docs/Timeline.md "wikilink") (from 2003 to 2006)
-   [Version History](/docs/Version_History.md "wikilink") (More detailed version history)
-   [Press Coverage](/docs/Press_Coverage.md "wikilink")
-   [Archive](/docs/Archive.md "wikilink")

External Links
--------------

-   [GoT Tweakers.net Topic \#1](http://gathering.tweakers.net/forum/list_messages/707958/0) (Dutch)
-   [GoT Tweakers.net Topic \#2](http://gathering.tweakers.net/forum/list_messages/714034/0) (Dutch)
-   [Video Archive](http://www.youtube.com/playlist?list=PL1C361986E95BCA42&feature=plcp) - Media from older MTA releases on Youtube.

References
----------

<references/>
[Category:Historical](/docs/Category:Historical.md "wikilink")

[pl:Multi\_Theft\_Auto](/docs/pl:Multi_Theft_Auto.md "wikilink") [es:Multi\_Theft\_Auto](/es:Multi_Theft_Auto.md "wikilink")

[1] Trilogy: Grand Theft Auto III, Grand Theft Auto: Vice City and Grand Theft Auto: San Andreas

[2] <http://hobby.estetiksoft.de/gta3console/html/getgta3console.htm>

[3] <http://www.un4seen.com/bass.html>

[4] <http://www.moddb.com/events/2011-mod-of-the-year-awards/features/moty-players-choice-mod-of-the-year>

[5] <http://forum.mtasa.com/viewtopic.php?f=31&t=51863>

[6] <http://files.mtasa.com/web/mta_0.5_launch/051.htm>
