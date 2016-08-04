Before you start
----------------

First of all, please ensure your computer fits the requirements needed. Read the [Client Manual](/docs/client_manual.md "wikilink") page for further informations, or join us on IRC @ <irc://irc.multitheftauto.com/mta>

### Requirements

The hardware requirements for Multi Theft Auto: San Andreas are the same than on Windows. For software requirements, you need:

-   Wine (get it on your package manager (synaptic, apt, pacman, yum etc.); follow instructions [here](https://www.winehq.org/download/ubuntu) if you're using Ubuntu

(as of MTA 1.4.1 Ubuntu's default Wine package seems to be incompatible with Visual C++, which is required to install MTA)

-   Windows fonts installed:
    -   tahoma.ttf
    -   tahomabd.ttf
    -   verdana.ttf

Get them on the Internet, e.g. [fontonic.com](http://fontonic.com/)

Or get the zip archive with the 3 fonts here: [wine\_mta\_fonts.zip](http://www.4shared.com/zip/IsErUbQAba/wine_mta_fonts.html)

Install them in:

    ~/.wine/dosdevices/c:/windows/Fonts/

(~/ points to your user home folder on Linux, .wine is the default wineprefix)

Installing the game
-------------------

Download the MTA installer from [mtasa.com](http://www.mtasa.com), ensure you can launch it (chmod +x) then install it when you want.

Running the game
----------------

Once installed, double-clicking on the Multi Theft Auto.exe should work. If not, try in a terminal the following command: “wine Multi Theft Auto.exe” in the directory you installed Multi Theft Auto to. If it doesn't work, check the contents of the file c:/Program\_Files/Multi Theft Auto/MTA/CEGUI.log, which may contain useful information.

Known issues
------------

### Specific issues

-   Impossible connection through the server browser \[Fixed in the [5084 bug](http://bugs.mtasa.com/view.php?id=5084) \]

<!-- -->

-   MTA won't start on Ubuntu 12.04 LTS \[Temporary fix is available [here](http://forum.mtasa.com/viewtopic.php?p=434011#p434011) \]

### Other issues

-   MTA isn't starting (even with fonts installed)

1.  Try to start MTA:SA in a virtual desktop
      
    Go to WineConfig, choose the tab “Graphics” and select “Emulate a virtual desktop”.

2.  Try to delete your gta\_sa.set file
      
    which is located in the “GTA San Andreas User Files” folder, which can be found in your home directory.
    **(Remember to create a copy, if you're playing San Andreas in singleplayer)**

3.  Try to delete your MTA config file
      
    which is: “MTA San Andreas 1.3/MTA/coreconfig.xml”
    **(Also remember to create a copy, if you don't want to lose your edited MTA configuration)**

-   Crash when connecting
      
    Sometimes the audio-server makes problems (could be related to pulseaudio), in this case you've to go to WineConfig and choose the tab Audio, then deselect “ALSA” and select “EsoundD”. Save the settings and restart MTA.

-   Crash in basswma.dll module while streaming audio
      
    Install Windows Media Player 10

<!-- -->

    winetricks wmp10

-   Special Detections (SD)
      
    If you are using a 64 wine version you may have problems with [Special Detections](http://wiki.multitheftauto.com/wiki/Anti-cheat_guide#.3Cenablesd.3E.3C.2Fenablesd.3E). If the server you are trying to connect keeps showing something like [this](http://i.imgur.com/33T8a82.jpg), then you should make a [32 bit wine prefix](http://wiki.archlinux.org/index.php/Wine#Using_WINEARCH) (or bottle).

<!-- -->

    export WINEARCH=win32 WINEPREFIX=~/.winegta
    winecfg

Change Windows version on bottom to Windows 7 and press OK. Now you have a 32 bit wine prefix on ~/.winegta. Install GTA:SA and them MTA. After this, MTA and GTA have been installed within ~/.winegta prefix which is a 32 bit wine environment.

See Also
--------

-   [nightly.mtasa.com](http://nightly.mtasa.com/) - For nightly builds.
-   <https://bugs.mtasa.com/view.php?id=8895> - a bug report containing useful info for running MTA in Wine

[Category:Support](/docs/category-support.md "wikilink") [ru:Client on Linux Manual](/docs/ru-client_on_linux_manual.md "wikilink") [hu:Client on Linux Manual](/docs/hu-client_on_linux_manual.md "wikilink")
