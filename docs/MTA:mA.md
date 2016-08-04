Introduction
------------

Multi Theft Auto: mIRC Admin (MTA:mA) is an admin client for MTA developed by *Aeron* in [mIRC](http://www.mirc.com). It has the possibility to create and run custom-made mIRC scripts on MTA servers, useful for creating gamemodes, whilst providing other functions such as cheat protection and links to other programs.

History
-------

### v1 series

It all started back in the MTA:VC 0.2.2 days. A normal player nicknamed *Aeron* drives around on his *PCJ600* and sees some other players racing 'orginized' racing. He joins the club and did some races. The only problem was that the countdown of 5 wasn't really smooth and the player who's typing it was always the first to start or the last. *Aeron* wondered if there was not a possibility to get some sort of script running that does the countdown that gets triggerd with '!count'. After some searching he realized there was no such ability. Therefore he decided to make his own. With use of *Ethereal* he sniffed around in the packets that MTA sends and note them down. He saw that the packets were not encoded and that there was some sort of structure. After creating alot of mIRC-scripts over the years, he created one to connect with a MTA server as a client and named it *MTA Connection Script*. After some scripting he could finally create his very wanted '!count'-script:

` alias mta.text {`
`   if ($2 == !count) {`
`     mta.say Count down!`
`     .timer9 1 1 mta.say 5`
`     .timer8 1 2 mta.say 4`
`     .timer7 1 3 mta.say 3`
`     .timer6 1 4 mta.say 2`
`     .timer5 1 5 mta.say 1`
`     .timer4 1 6 mta.say GOGOGO!`
`   }`
` }`

Later he made a post of it on MTA forums which can be found [here](http://forum.mtasa.com/viewtopic.php?t=5362). After some positive replies, he decided to continue work on it. But after [this](http://forum.mtasa.com/viewtopic.php?p=53791) post and a PM to *Blokker\_1999* about the netcode the MTA team realized this could go wrong as you can see in *Blokker\_1999*'s reply on the PM:

` WE HATE HACKERS!`

*MrBump* made a suggestion to make it Admin only and *MrBump* became *Aeron*'s contact person and advisor about the script. *Aeron* renamed the script to *MTA Admin Control* and had a warm welcome in this [post](http://forum.mtasa.com/viewtopic.php?p=54788) after there where handy scripts running on some popular servers.

A couple of days later when MTA:VC 0.3 was released posted *MrBump* a frontpage post when *MTA Admin Control* v1.18 was ready for release, but he decided to release it under the name *MTA mIRC Admin*.

MTA:mA v1.21 is the latest version for MTA:VC 0.3.

|                                                                                 |                                                                                 |                                                                                                    |
|---------------------------------------------------------------------------------|---------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------|
| [thumb|none|200px|MTA Connection Script v0.1](/Image:MTACS01.gif.md "wikilink") | [thumb|none|200px|MTA Connection Script v0.2](/Image:MTACS02.GIF.md "wikilink") | [thumb|none|200px|Scripting component of MTA Admin control v0.1](/Image:MTACS03.gif.md "wikilink") |
| [thumb|none|200px|MTA Admin Control v0.1](/Image:MTAMA01.gif.md "wikilink")     | [thumb|none|200px|MTA Admin Control v0.2](/Image:MTAMA02.gif.md "wikilink")     | [thumb|none|200px|MTA mIRC Admin v1.12](/Image:MTAMA112.gif.md "wikilink")                         |
| [thumb|none|200px|MTA mIRC Admin v1.20](/Image:MTAMA120.gif.md "wikilink")      | [thumb|none|200px|MTA mIRC Admin v1.221](/Image:MTAMA1221.gif.md "wikilink")    | [thumb|none|200px|MTA mIRC Admin v1.222](/Image:MTAMA1222.gif.md "wikilink")                       |

### v2 series

This version got released when MTA:VC 0.3.1 came out and came with wildcard IP management, an auto updater, new game 'modes' and a few other little things.

MTA:mA v2.013 is the latest version for MTA:VC 0.3.1.

|                                                                                |                                                                              |
|--------------------------------------------------------------------------------|------------------------------------------------------------------------------|
| [thumb|none|200px|MTA mIRC Admin v2.0 Alpha](/Image:MTAMA2A.gif.md "wikilink") | [thumb|none|200px|MTA mIRC Admin v2.005](/Image:MTAMA2005.gif.md "wikilink") |

### v3 series

This version was released when MTA:VC 0.4 came out and came with PM dialogs, GTA:3 support, Admin+, map function and other little things. Over time, MTA:VC 0.5 support, multiple script support and zoom function for the map were added.

MTA:mA v3.24 is the latest version for MTA 0.4, MTA 0.5, and MTA 0.5r2.

|                                                                         |                                                                            |
|-------------------------------------------------------------------------|----------------------------------------------------------------------------|
| [thumb|none|200px|MTA mIRC Admin v3.24](/Image:mtama.JPG.md "wikilink") | [thumb|none|200px|MTA mIRC Admin v3.07](/Image:MTAMA307.gif.md "wikilink") |

### v4 series

This version was released when MTA:SA 1.0 came out and is very limited, like the previous MTA:MAs.

MTA:mA v4.12 is the latest version for MTA:SA 1.0

|                                                                            |                                                                                             |
|----------------------------------------------------------------------------|---------------------------------------------------------------------------------------------|
| [thumb|none|200px|MTA mIRC Admin v4.06](/Image:MTAMA406.png.md "wikilink") | [thumb|none|200px|Map component of MTA mIRC Admin v4.12](/Image:MTAMA412.png.md "wikilink") |

Scripts
-------

There are hundreds of scripts for MTA:mA. These are the most popular ones:

### MTA:mA:GRS

A very popular script is *MTA:mA:GRS* (*General Release Script*, developed by Oliver Brown (\[FMJ\]Oli), which is widely used in both *[GTA3:MTA](/GTA3MTA_0.5.md "wikilink")* and *[MTA:VC](/MTAVC_0.5.md "wikilink")* servers.

[300px|center|thumb|General Release Script / GRS](/Image:grs.JPG.md "wikilink")

### Clan RPG Script

A Clan RPG Script developed by \[FMJ\]Oli and *Jax* Features:

`Cash/Bank System`
`Clan/Player Registration`
`Item/Vehicle/Property Purchasing/Selling`
`Robbing Capability`
`GTA3/VC Support`
`Various Bug/Error Fixes - Speed Improved`
`King of the House Mode`
`Cash/Item Stashing`
`Bounty Hunting`
`District/City Purchasing/Selling`
`Petrol Buying/Using/Effects `

The orginal forum thread can be found [here](http://forum.mtasa.com/viewtopic.php?t=11562).

Links
-----

-   [MTA:mA - Homepage](http://home.deds.nl/~aeron/)
-   [More MTA:mA screenshots](http://files.mtasa.com/web/mtama_history/)
-   [MTA:mA v1.21](http://files.mtasa.com/apps/tools/MTAmA/MTAmA121.zip) [Mirror](http://www.projectredivivus.com/files/tools/MTAmA/MTAmA121.zip)
-   [MTA:mA v1.222](http://files.mtasa.com/apps/tools/MTAmA/MTAmA1222.zip) [Mirror](http://home.deds.nl/~aeron/mtama/1.0/MTAMA1222.rar)
-   [MTA:mA v2.004](http://files.mtasa.com/apps/tools/MTAmA/MTAmA2004.zip) [Mirror](http://www.projectredivivus.com/files/tools/MTAmA/MTAmA2004.zip)
-   [MTA:mA v2.013](http://files.mtasa.com/apps/tools/MTAmA/MTAmA2013.zip) [Mirror](http://home.deds.nl/~aeron/mtama/2.0/MTAMA2013.rar)
-   [MTA:mA v3.00](http://files.mtasa.com/apps/tools/MTAmA/MTAmA300.zip) [Mirror](http://www.projectredivivus.com/files/tools/MTAmA/MTAmA300.zip)
-   [MTA:mA v3.04](http://files.mtasa.com/apps/tools/MTAmA/MTAmA304.zip) [Mirror](http://www.projectredivivus.com/files/tools/MTAmA/MTAmA304.zip)
-   [MTA:mA v3.08](http://files.mtasa.com/apps/tools/MTAmA/MTAmA308.zip) [Mirror](http://www.projectredivivus.com/files/tools/MTAmA/MTAmA308.zip)
-   MTA:mA v3.11
-   [MTA:mA v3.18](http://files.mtasa.com/apps/tools/MTAmA/MTAmA318.zip) [Mirror](http://www.projectredivivus.com/files/tools/MTAmA/MTAmA318.zip)
-   [MTA:mA v3.19](http://files.mtasa.com/apps/tools/MTAmA/MTAmA319.zip) [Mirror](http://www.projectredivivus.com/files/tools/MTAmA/MTAmA319.zip)
-   [MTA:mA v3.23](http://files.mtasa.com/apps/tools/MTAmA/MTAmA323.zip) [Mirror](http://www.projectredivivus.com/files/tools/MTAmA/MTAmA323.zip)
-   [MTA:mA v3.24](http://files.mtasa.com/apps/tools/MTAmA/MTAmA324.zip) [Mirror](http://www.projectredivivus.com/files/tools/MTAmA/MTAmA324.zip)
-   [MTA:mA v4.00](http://files.mtasa.com/apps/tools/MTAmA/MTAmA4.zip) [Mirror](http://www.projectredivivus.com/files/tools/MTAmA/MTAmA4.zip)
-   [MTA:mA Series 1 Downloads](http://home.deds.nl/~aeron/mtama/1.0/)
-   [MTA:mA Series 2 Downloads](http://home.deds.nl/~aeron/mtama/2.0/)
-   [MTA:mA Series 3 Downloads](http://home.deds.nl/~aeron/files/)
-   [MTA:mA Series 4 Downloads](http://home.deds.nl/~aeron/mtama/4.0/)
-   [MTA:mA Series 4 Maps](http://files.mtasa.com/apps/tools/MTAmA/maps.zip) [Mirror](http://www.projectredivivus.com/files/tools/MTAmA/maps.rar) [Mirror \#2](http://web.archive.org/web/20060424164026/http://talidan.littlewhitey.net/mtama/maps.rar)
-   [MTA:mA - General Release Script - MTA Forum Topic](http://forum.mtasa.com/viewtopic.php?t=8788%20)
-   [MTA:mA - General Release Script 4.14](http://files.mtasa.com/apps/tools/MTAmA/MTAmA_GRS_4.14.exe) [Mirror](http://www.projectredivivus.com/files/tools/MTAmA/MTAmA_GRS_4.14.exe) [Mirror \#2](http://web.archive.org/web/20071102021213/http://www.mta-fmj.com/mtama.exe)
-   [MTA:mA - General Release Script 4.03 - Manual](http://files.mtasa.com/apps/tools/MTAmA/GRS_MANUAL_4.03.txt) [Mirror](http://www.projectredivivus.com/files/tools/MTAmA/GRS_MANUAL_4.03.txt)
-   [MTA:mA - General Release Script 4.04 - Manual](http://files.mtasa.com/apps/tools/MTAmA/GRS_MANUAL_4.04.txt) [Mirror](http://www.projectredivivus.com/files/tools/MTAmA/GRS_MANUAL_4.04.txt)
-   [MTA:mA - General Release Script 4.14 - Manual](http://files.mtasa.com/apps/tools/MTAmA/GRS_MANUAL_4.14.txt) [Mirror](http://www.projectredivivus.com/files/tools/MTAmA/GRS_MANUAL_4.14.txt)

[Category:MTA 0.5](/Category:MTA_0.5.md "wikilink") [Category:Historical](/Category:Historical.md "wikilink")
