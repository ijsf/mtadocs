This applies to MTA 0.5r2 (both GTA3:MTA and MTA:VC). The known issues for MTA:SA 1.x can be found [here](/docs/known_issues_-_faq.md "wikilink").

Client issues:
--------------

-   **Australian and German EXEs (and possibly others) may produce an “invalid executable” error when you try to start a game.**

As Australian and German EXEs don't work reliably with MTA, this shouldn't be a huge problem. Try to obtain a standard EXE. You can try [**Talidan**'s invalid executable patcher](http://forum.mtasa.com/viewtopic.php?f=50&t=12180).

-   **Crash when MTA:VC DM is loading.**

Make sure you run GTA3 or Vice City at least once in single player without MTA before actually running it with MTA. If that doesn't work, try [the Vice 1.1 patch](http://updates.rockstargames.com/patches/vicecity/vicepatch_11.zip). If that still doesn't work, post in [the support forum](http://forum.mtasa.com/viewforum.php?f=50).

-   **Freeze when the client tries to display dialog asking for game path.**

There have been a couple of occurrence of this, and we'd be interested to see why this is. You can avoid it by manually setting the path in the mta.ini in the Multi Theft Auto directory.

For Vice City, your mta.ini should contain (replace the path if necessary):

    [Game-VC]
    Version=0
    Location=C:\Program Files\Rockstar Games\Grand Theft Auto Vice City\gta-vc.exe

For GTA3:MTA, your mta.ini should contain (replace the path if necessary):

    [Game-GTA3]
    Version=1
    Location=C:\Program Files\Rockstar Games\GTAIII\gta3.exe

-   **XFire crashes game during loading.**

Both XFire and MTA use similar methods for integrating themselves into the game. We've contacted XFire to offer our support for them in implementing support for MTA, but they haven't responded. If you wish to use XFire in MTA, contact XFire. In the meantime, disable XFire before you play.

-   **MTA claims “Suspected Trainer Usage.”**

Try closing every other open window first, then if that doesn't work restart MTA. If that doesn't work, try reinstalling MTA 0.5r2.

-   **You join a server and are told you are banned, even though you aren't in the ban list.**

The cause of this is unknown. You may be banned by a over-general ban in the server's ban list.

-   **Client crashes when you join a server.**

This crash may be caused by the client trying to download the rich text MOTD specified by the server and failing (e.g. the site its trying to get it from is down, or the URL is invalid). If this happens, the client will crash.

-   **You have quite a few files on your computer called mtachat.txt.**

mtachat.txt, as you probably guessed, stores a chat log. This feature was added at the last moment and not properly tested. Consequently, this problem has occurred. This is probably due to how the client has been launched (the start path determines where it saves the chat, not the install path). Feel free to delete any files you don't want.

-   **Upon clicking “Start Game” the client informs you your client is modified.**

Click **Start Game** again.

-   **When playing GTA3 you receive an “Invalid Executable” error.**

This is probably because you are using GTA3 version 1.0 instead of 1.1. You can get the GTA3 1.1 patch [here](http://updates.rockstargames.com/patches/grandtheftauto3/GTA3patch1.1.zip). If this doesn't work, or you already have GTA3 1.1, make sure you have the USA/UK EXE; you can try **Talidan**'s [invalid executable patcher](http://forum.mtasa.com/viewtopic.php?f=50&t=12180). Failing that, try to obtain one elsewhere.

-   **Your virus scanner informs you that the Multi Theft Auto 0.5r2 executable is a virus or malware.**

MTA does <u>not</u> contain any viruses, malware, adware or spyware. It is flagged as a false positive because of the way the executable is packed. Ensure you only download the client from our site. [This link](http://dl.dropbox.com/u/12783812/mta05r2_full_installer.exe) is uploaded by our account. Use this if you doubt the validity of your copy of MTA.

-   **You get a crash at the address 652F30 when starting the game.**

Ensure your game language is set to English.

Gameplay issues:
----------------

-   **MTA:VC (either map) crashes when you try to get on a motorcycle as passenger when it has no driver, as well as a couple other crashes in certain circumstances with motorcycles**

Sorry, I was unable to fix this for 0.5r2. This may be fixed in a future release.

-   **MTA:VC DM: You are unable to jump or sprint when a Molotov is your active weapon, but you are able to jump and sprint with Grenades**

This will be fixed in a future release if there is one.

-   **MTA:VC (either map): after exiting spectator mode, you may see a brief glimpse of Tommy falling and potentially receiving fall damage; once you spawn with a skin, you have less than 100 health**

This will be fixed in a future release if there is one.

-   **GTA3:MTA, Turismo/Shoreside Scramble gamemode: During a race, if another racer dies, every living racer crashes.**

I was also unable to fix this issue for 0.5r2. This may be fixed in a future release.

-   **GTA3:SSV, Van Heist gamemode: The home base marker flickers, and if the Securicar explodes, then the damage meter shows negative**

Live with it, neither were worth my time to fix for 0.5r2. This may be fixed in a future release.

Server issues:
--------------

-   **You receive the error “ERROR: The ServerName, ServerPort, GameMap, GameHour, GameMins, Weather and BannedFile MUST be specified in the configuration file” when you run your server, and all fields are filled in. *Only affects Server Patch 1 Hotfix***

Ensure that your server name is 49 characters or less. This is a misleading error.

-   **Your client times out as soon as you connect to a server. Players all time out when they connect to your server.**

This has been an unknown problem for quite some time now, but it seems it is caused not by MTA or the MTAServer but by MTA:mA, or more specifically scripts running on it. If the scripts send multiple messages to the player when they join it is highly likely to time them out. This results in nobody being able to play.

For now a fix is available for MTA:mA [here](http://forum.mtasa.com/viewtopic.php?p=181919#181919) (hopefully GRS will also be updated soon).

Please follow **Aeron**'s instructions regarding its use.

A big thank-you to **Mike** for discovering the cause of this problem and **Aeron** for getting a fix out so quickly.

[ru:MTA\_0.5r2\_Known\_Issues](/docs/ru:mta_0.5r2_known_issues.md "wikilink")

[Category:Vice\_City](/docs/category:vice_city.md "wikilink") [Category:GTA3](/Category:GTA3.md "wikilink") [Category:MTA\_0.5](/Category:MTA_0.5.md "wikilink")
