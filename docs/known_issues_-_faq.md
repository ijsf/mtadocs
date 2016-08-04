Post here your proposed Q&A, regarding the known problems with MTA:SA and their solutions, especially the problems we are encountering now, that might be also encountered by users in the final release. You are also welcome to edit them grammar/style wise.

-   [Map editor FAQ/known issues can be found here.](/docs/resource:editor#faq.md "wikilink")
-   [Known issues for MTA 0.5r2 can be found here.](/docs/mta_0.5r2_known_issues.md "wikilink")

Client
------

### General

#### I have the Steam version of GTA San Andreas. How can I play MTASA?

  
The Steam version of GTASA is currently incompatible with MTASA, just like it is with some other mods. However, it can be made to work with it.

<!-- -->

  
**If you just want to play the newest version of the mod, all you need to do is download the mod from our home page and then install it**. The installer will detect your Steam's GTASA installation and will make some adjustments automatically.

No original files are modified in the process, so the single player mode will work the same way as it did before.

<!-- -->

  
If you want to play some older MTA:SA version (1.3.2 or older), follow a few simple steps, and the Steam version will be compatible with it:

-   **Option 1:** Find a **GTA SA 1.00 No CD** (Google will give useful results). You should obtain a 1.00 Cracked/NoCd EXE, not a Disc image. Any HOODLUM release will work fine.
    -   Open the download with Winrar or other similar archive tools, and inside there should be a gta\_sa.exe. Place this file inside your installation directory. This is normally **C:\\Program Files\\Steam\\steamapps\\common\\grand theft auto san andreas**. No files need to be replaced during this process.

This procedure will not affect your Steam version of GTASA, but will allow MTASA to boot alongside it.

-   **Option 2:** Use the unofficial [steam downgrade patch](http://forums.steampowered.com/forums/showthread.php?t=1952458), be sure to downgrade to 1.0 and not 1.01.

#### Does MTASA work with v1.01 or v2.00 of GTA San Andreas?

  
No. It can be made to work with them however - please see [this forum topic](http://forum.multitheftauto.com/viewtopic.php?t=15151) for instructions on patching the exe.

#### Initial black screen/hanging GTA splash screens

:\* **MTA shows a permanent black screen or hanging GTA splash screens.**

  
It may be necessary that during/after the logo splash screens in Grand Theft Auto you have to give some input in order to skip the videos correctly. Try to click your left-mouse button a few times, or tapping a few keys.

:\* **MTA shows a permanent black screen after the GTA splash screens (possibly with text in the bottom right corner).**

  
This can be related to a lack of support for DirectX or video card features, on your system, which are needed to run the dynamically rendered menu. This dynamic menu is enabled by default. You can disable it by opening your [coreconfig.xml](/docs/coreconfig.xml.md "wikilink") configuration file located in the *GTA San Andreas\\MTA* directory, and changing the value of *menu\_options* to *248*.

#### Halt after MTA splash screen

:\* **Nothing happens after the 'Stop playing with yourself' splash screen**

  
If you use nVidia GeForce, try turning off nView Desktop Manager before starting MTA.

<!-- -->

  
Also try deleting GTA San Andreas settings file (“gta\_sa.set”) in “Documents\\GTA San Andreas User Files” folder.

<!-- -->

  
If it all fails and you run Kaspersky Anti-Virus or Internet Security, make sure status of “multi theft auto.exe” in not restricted. Other anti-virus software may block MTA from running.

#### Crash after MTA splash screen

:\* **MTA crashes after the 'Stop playing with yourself' logo. Both single player and the MTA: Race ran fine before.**

  
Try downloading the latest DirectX Runtime files from [Microsoft](http://www.microsoft.com/downloads/details.aspx?FamilyID=2da43d38-db71-4c1b-bc6a-9b6652cd92a3&DisplayLang=en). Also check in Task Manager, if :gta\_sa.exe process isn't already running.

<!-- -->

  
If you run at any substandard resolutions (e.g. 960x720), try to change your resolution to a commonly supported one (e.g. 640×480, 800×600, 1024×768, 1152×864, 1280×1024) by launching Grand Theft Auto: San Andreas in normal mode, setting the new resolution and exiting.

<!-- -->

  
If you are a user of Windows Vista or Windows 7, try the following:

-   Enable Windows XP SP3 compatiblity mode for both Multi Theft Auto.exe and gta\_sa.exe, setting their privilege level to “Run this program as an administrator”.
-   Configure Data Execution Prevention: Use the setting *Turn DEP for all programs and services except those I select*. Click *add* and find “Multi Theft Auto.exe” and “gta\_sa.exe” and add them.
-   Run MTASA as administrator.

#### “Data files have been modified”

:\* **You receive an error stating “San Andreas data files have been modified”**

  
You can fix this by [installing this patch](http://updatesa.mtasa.com/sa/files/GTASA-data-1.0.4.exe). If that doesn't work, try reinstalling GTA San Andreas.

#### Crash after connecting to any server

:\* **MTASA crashes upon connecting to any server. Single player runs fine.**

  
Single player mods can affect the way MTA:SA works, potentially causing crashes - you should always use a clean GTASA install for MTA:SA.

<!-- -->

  
This might also occur on non-modded installs, when your GTASA executable is in an unsupported by MTA:SA version (eg. 1.0 German or Australian). To resolve this, use [our converter](http://forum.multitheftauto.com/viewtopic.php?f=89&t=15151).

#### Controls not working

:\* **My controls don't seem to work as they should.**

  
Try using the 'copygtacontrols' command in the console.

#### Incorrect models

:\* **Woman model's breasts look awkward ingame / I'm seeing odd, spider-like shaped player models.**

  
This is caused by the way GTA handles player stats. To fix this, be sure to set both fat and muscles player stats to 0, when you're changing player skin.

#### Incorrect drive-by functionality

:\* **Drivebys arent working as they should**

  
Drivebys are handled by script, and will change depending on the loaded gamemode.

#### Unsaved settings

:\* **My MTA setting(s) didn't get saved (...) I crashed.**

  
First, configure the MTA the way you want to, then exit the game and launch it again. Settings should get saved. Alternatively, try removing the coreconfig.xml file, then configure it and quit the game.

#### Gamepad support

:\* **MTA doesn't recognise my gamepad**

  
Ensure that your controller is the first controller recognised by Windows (MTA will only use the first controller). You can configure your gamepad in options in MTASA's main menu.

#### Free mouselook not working properly

:\* **MTA doesnt recognise my mouse**

  
Some people got problems with their mouse in MTA. They can use it in the menu, connect to a server, but they can't use the mouse for free look.

This problem can be solved by entering a server, click your Win/Windows key at your keyboard once, and then click your mouse.

If that doesn't work try starting GTA in Singleplayer, go to options &gt; controler setup and set “Configuration” to “Mouse + Keys” instead of “Joypad”.

#### Server browser not working

:\* **The in-game server browser shows “Loading” but does not come up with any servers**

  
Depending on the type and status of the internet connection you are using, it can take up to a few seconds for the server browser to retrieve all the servers. Please wait a little longer for the results to appear.

<!-- -->

  
If all else fails, you can logon to [GameMonitor](http://www.game-monitor.com/search.php?game=mta), and click the green play icon to play on that server.

#### Invalid serial number

:\* **I am getting an 'Invalid serial number' error when trying to launch or play the game**

  
You are running an outdated version of Multi Theft Auto. Head over to the [main page](http://mtasa.com/) and download the latest version of Multi Theft Auto.

#### 'Network module not compatible!' on MTA:SA launch

:\* '''I am getting 'Network module not compatible!' error message upon launching MTA:SA

  
This could mean that your MTA:SA install is incomplete or broken. Reinstall it.

#### 'No such mod installed (deathmatch)'

:\* '''I am getting a 'No such mod installed (deathmatch)' error message when trying to connect to any server

  
**Option 1:** Simply re-install MTA.

**Option 2:** Run both gta\_sa.exe and Multi Theft Auto.exe with administrator privileges.

#### D3dx9\_\*\*.dll is not found

:\* '''When I start Multi Theft Auto: San Andreas I am getting an error D3dx9\_\*\*.dll (\*\* = a number) cannot be found.

  
This means that DirectX 9 is not installed or not up to date.

To install/update DirectX download the [DirectX End-User Runtime Web Installer](http://www.microsoft.com/downloads/details.aspx?displaylang=en&FamilyID=2da43d38-db71-4c1b-bc6a-9b6652cd92a3) from the Microsoft download site.

#### CRC mismatch

:\* '''When joining a server, the chatbox shows 'CRC mismatch'

  
This is a server problem. Tell the owner to look at the server section of this page.

#### 'Error loading netc.dll module! (Error 14001)' on MTA:SA launch

:\* Full error message:

  
*Error loading netc.dll module! (Error 14001: The application has failed to start because its side-by-side configuration is incorrect. Please see the application event log for more detail.)*

<!-- -->

  
Make sure you have installed Microsoft Visual C++ 2008 regular and SP1 redistributable packages (x86):

<!-- -->

  
[Microsoft Visual C++ 2008 Redistributable package (x86)](http://www.microsoft.com/downloads/details.aspx?FamilyID=9b2da534-3e03-4391-8a4d-074b9f2bc1bf&displaylang=en)

<!-- -->

  
[Microsoft Visual C++ 2008 SP1 Redistributable package (x86)](http://www.microsoft.com/download/en/details.aspx?id=5582)

#### 'Error 1935. An error occurred during the installation of assembly 'Microsoft.VC90.ATL...'

  
Download the 'Fix it' helper from here: [1](http://support.microsoft.com/default.aspx?scid=kb;en-us;946414)

#### Your virus scanner warns you about MTA:SA

:\* **Your virus scanner informs you that the MTA:SA or setup executable is a virus or malware.**

  
MTA does **NOT** contain any viruses, malware, adware or spyware. You should re-download MTASA [here](http://mtasa.com) if you doubt the validity of your copy of MTA.

#### When downloading large maps, progress halts

:\* **When downloading large maps, progress often halts, while transmission is still taking place.**

  
This issue is fixed in [MTA:SA 1.3](http://forum.mtasa.com/viewtopic.php?f=31&t=39555#p402093).

### Windows Vista® / Windows 7-specific

#### Crash on connect

:\* **I seem to crash whenever I connect to a server just before I go in-game on Vista**

  
This seems to be an issue with the Microsoft DirectX April 2006 SDK Redistributable DLL file (d3dx9\_30.dll) when running in compatibility mode. Please make sure that compatibility mode is competely turned off for **both** your GTA\_SA.exe and Multi Theft Auto.exe executables.

#### Clock manipulation error

:\* '''I am getting 'Clock manipulation detected!' error message upon launching MTA:SA

  
This is caused by incorrect system date/time being set (which could be a result of wrong settings or a faulty battery on the pc's motherboard). Setting time and date again should fix the problem.

<!-- -->

  
It might also happen if you are using an AMD Athlon 64 X2 processor with some old drivers. Update them at [AMD's site](http://support.amd.com/us/Pages/drivers.aspx).

#### Halt on launch

:\* '''When I launch MTA:SA, nothing happens (GTA\_SA.exe is running but not loading up)

  
Run MTA:SA with Administrator privileges. To do this, right click on the installer executable, choose 'Properties', go into 'Compatibility' tab and tick the check box on the last field and try again.

#### General GTA problems

:\* **I have unexplainable GTA problems or crashes**

  
Make sure your computer as well as your GTA install meet the [minimum requirements](/docs/deathmatch_client_manual#system_requirements.md "wikilink") and that you are not running in any 98/2000/XP/2003 compatibility modes.

<!-- -->

  
Also try the solutions from these pages:

-   <http://www.gtaforums.com/index.php?showtopic=273549&view=findpost&p=4537502>
-   <http://pullmonkey.com/2007/4/30/how-i-got-gta-san-andreas-to-work-with-a-crappy-os-vista>

#### Performance Issues Sandy Bridge / Second Generation Intel Core

:\* **Slow MTA performance on Sandy Bridge Processors while other games and San Andreas Singleplayer run fine.**

  
There seems to be a issue in combination with the Windows power profile running in power saving mode, you can solve this issue by changing the power profile to high performance when playing MTA:SA.

-   Topic about this issue: [Sandy Bridge performance issues?](http://forum.mtasa.com/viewtopic.php?f=104&t=31745)

Server
------

### General

#### Fatal error 3

:\* **I'm getting *Fatal Error 3* whenever I connect to my server**

  
This error happens when the server you are trying to connect to is unable to provide you the required downloads, because it does not have http downloading enabled. Be sure to set the **httpdownload** configuration tag in your configuration to **1**.

#### Download error 9: Error downloading requested files

:\* **I'm getting *Download Error 9: Error downloading requested files* whenever I connect to my server**

  
This error happens when the server you are trying to connect to is unable to provide you with a valid link. This results in a 404 (Not found) HTTP error and an error at your end.

:\* If you are running the built-in server (**httpserver** is set to **1** and **httpdownloadurl** is empty), make sure that your HTTP server is accessible (you can try to access it by using a browser) for everyone.

:\* If you have configured an external web server (**httpdownloadurl** is set to your custom URL), make sure that your HTTP is accessible and make sure you have read the [Configuring an external web server](/docs/deathmatch_server_manual#configuring_an_external_web_server.md "wikilink") guide.

#### CRC mismatch

:\* '''When clients join my server, their chatbox shows 'CRC mismatch'

  
CRC mismatch occurs when either:

-   The server files have been changed, but the resource has not been restarted/refreshed
-   An external http server is being used and the files are not synchronized

#### Accounts missing

  
The file *accounts.xml* is not used from 1.0.4, it has been replaced by a file called *internal.db*. To ensure your old accounts information is migrated:

-   Stop the server
-   Make sure your old *accounts.xml* is correct
-   Delete *internal.db*
-   Start the server

#### Resources missing

  
From 1.0.4, resource names cannot contain dots.

#### Download error 28

  
Try closing anti-virus or firewall applications. If it then works, try adding an exception to your firewall to allow your http port through.

#### Accounts disappearing

  
Account information (or anything else) not being saved correctly can be caused by database corruption. From build 2836, the server checks the integrity of the sqlite database files on startup. If it reports a database error, please read [How to repair the database files](/docs/how_to_repair_the_database_files.md "wikilink").

If you are running an earlier version and are having troubles such as accounts disappearing, you should upgrade your server to the [lastest build](http://nightly.multitheftauto.com/)

### Windows-related

  
No known reported issues in .

### Linux-related

#### Default nohup creates infinitely big nohup.out

  
Temporary fix, disable the nohup file: 'nohup ./mta\_server &gt; /dev/null &'

[es:Problemas Conocidos - FAQ](/docs/es:problemas_conocidos_-_faq.md "wikilink") [it:Bugs noti e FAQ](/docs/it:bugs_noti_e_faq.md "wikilink") [ru:Known Issues - FAQ](/docs/ru:known_issues_-_faq.md "wikilink") [de:Known Issues - FAQ](/docs/de:known_issues_-_faq.md "wikilink") [pt-br:Soluções de Problemas - FAQ](/docs/pt-br:soluções_de_problemas_-_faq.md "wikilink") [hu:Known Issues - FAQ](/docs/hu:known_issues_-_faq.md "wikilink") [zh-cn:已知问题 - 常见问题](/docs/zh-cn:已知问题_-_常见问题.md "wikilink")

[Category:Support](/docs/category:support.md "wikilink")
