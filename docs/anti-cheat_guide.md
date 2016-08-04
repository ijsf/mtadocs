Server setup
============

3 settings in [**mtaserver.conf**](/docs/server_mtaserver.conf.md "wikilink") control AC behaviour for a server:

<disableac></disableac>
-----------------------

Comma separated list of disabled anti-cheats. This setting disables specific AC codes. AC codes are shown to the player when that detection has been triggered. Available codes are:

| Code for <disableac> | Displayed on detect | Required server version | Required <minclientversion> | Notes                                                                                                                                        |
|----------------------|---------------------|-------------------------|-----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| **1**                | AC \#1              | any                     |                             | Classic health/armour hack detector                                                                                                          |
| **4**                | AC \#4              | any                     |                             | Detects presence of trainer. Capital letters in the message are for tagging particular trainers                                              |
| **5**                | AC \#5              | any                     |                             | Detects use of trainer.                                                                                                                      |
| **6**                | VF \#6              | any                     |                             | Detects use of trainer incl.: player movement, health/damage, weapons, money, gamespeed, game cheats, aimbot                                 |
| **7**                | VF \#7              | any                     |                             | Detects use of trainer.                                                                                                                      |
| **8**                | VF \#8              | any                     |                             | Detects unauthorized mods                                                                                                                    |
| **11**               | AC \#11             | any                     |                             | More trainers                                                                                                                                |
| VF \#11              | any                 |                         | Dll injector / Trainer      |
| **13**               | SD \#13             | any                     |                             | Data files issue                                                                                                                             |
| **17**               | VF \#17             | any                     |                             | Speed / wall hacks                                                                                                                           |
| **21**               | AC \#21             | any                     | 1.3.1-9.05097               | More trainers                                                                                                                                |
| VF \#21              | any                 | 1.3.1-9.05097           | Custom gta\_sa.exe          |
| **26**               | SD \#26             | any                     | 1.3.4-9.05858               | Anti-cheat component blocked &lt;!--                                                                                                         |
| **31**               | SD \#31             | any                     |                             | gta3.img player skin mods (1.4 only. For 1.5, use [allow\_gta3\_img\_mods](/docs/server_mtaserver.conf#allow_gta3_img_mods.md "wikilink")) --&gt; |

<enablesd></enablesd>
---------------------

Comma separated list of enabled special detections. A special detection is a type of anti-cheat for (usually) harmless game modifications. Competitive servers may wish to enable special detections, but most servers should leave this setting blank. Available codes are:

| Code for <enablesd> | Displayed on detect | Required server version | Required <minclientversion> | Notes                                                                                                                                                                                                                  |
|---------------------|---------------------|-------------------------|-----------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **12**              | SD \#12             | any                     |                             | Disallow custom D3D9.DLL                                                                                                                                                                                               |
| **14**              | SD \#14             | 1.3.1-9.04605           | 1.3.1-9.04605               | Disallow virtual machines such as VMWare                                                                                                                                                                               |
| **15**              | SD \#15             | 1.3.1-9.04791           | 1.3.1-9.04791               | Disallow disabled driver signing                                                                                                                                                                                       |
| **16**              | SD \#16             | 1.3.1-9.05097           | 1.3.1-9.05097               | Disallow disabled anti-cheat components. This is triggered when an anti-cheat component can not start. It is usually due to some problem with the PC and might be fixed by a reboot. Can also be triggered by a virus. |
| **20**              | SD \#20             | 1.3.1-9.05097           | 1.3.1-9.05097               | Disallow non-standard gta3.img or gta\_int.img (For servers not using [onPlayerModInfo](/docs/onplayermodinfo.md "wikilink"))                                                                                               |
| **22**              | SD \#22             | 1.3.4-9.05884           | 1.3.4-9.05884               | Disallow resource download errors/corruption (Lua script files)                                                                                                                                                        |
| **23**              | SD \#23             | 1.3.4-9.05884           | 1.5.2-9.07911               | Disallow resource download errors/corruption (Non-Lua files e.g. png,dff)                                                                                                                                              |
| **28**              | SD \#28             | 1.3.4-9.05884           | 1.3.4-9.05884               | Disallow Linux Wine                                                                                                                                                                                                    |

<client_file name="data/carmods.dat" verify="0"/>
-------------------------------------------------

By default, clients may not join a server if they have customized GTA:SA data files. Adding one or more of the above lines excludes files from validation. The file names that can be used are:
\*“data/carmods.dat”

-   “data/animgrp.dat”
-   “data/ar\_stats.dat”
-   “data/melee.dat”
-   “data/clothes.dat”
-   “data/object.dat”
-   “data/default.dat”
-   “data/surface.dat”
-   “data/default.ide”
-   “data/gta.dat”
-   “data/surfinfo.dat”
-   “data/peds.ide”
-   “data/vehicles.ide”
-   “data/pedstats.dat”
-   “data/water.dat”
-   “data/txdcut.ide”
-   “data/water1.dat”
-   “models/coll/weapons.col”
-   “data/weapon.dat”
-   “data/plants.dat”
-   “anim/ped.ifp”
-   “data/furnitur.dat”
-   “data/procobj.dat”
-   “data/maps”

***Note 1:*** *“data/maps” represents all the files and directories within “data/maps”*
***Note 2:*** *“data/handling.cfg” is not included as it is always ignored by MTA because of the internal vehicle handling functions. [See here if you want to load custom handling.cfg files](/docs/handling.cfg.md "wikilink")*

Client
======

When joining a server, the server AC info is displayed in the client console (F8)
Example:
Server AC Info: \[Allowed client files: None\] \[Disabled AC: None\] \[Enabled SD: None\]

Disabled AC contains the contents of the server setting from <disableac></disableac>
Enabled SD contains the contents of the server setting from <enablesd></enablesd>
Allowed client files contains numbers to indicate which client files the server allows to be modified. The numbers represent these files:

-   1 - “data/carmods.dat”
-   2 - “data/animgrp.dat”
-   4 - “data/ar\_stats.dat”
-   5 - “data/melee.dat”
-   6 - “data/clothes.dat”
-   7 - “data/object.dat”
-   8 - “data/default.dat”
-   9 - “data/surface.dat”
-   10 - “data/default.ide”
-   12 - “data/gta.dat”
-   13 - “data/surfinfo.dat”
-   14 - “data/peds.ide”
-   15 - “data/vehicles.ide”
-   16 - “data/pedstats.dat”
-   17 - “data/water.dat”
-   18 - “data/txdcut.ide”
-   19 - “data/water1.dat”
-   20 - “models/coll/weapons.col”
-   21 - “data/weapon.dat”
-   22 - “data/plants.dat”
-   23 - “anim/ped.ifp”
-   24 - “data/furnitur.dat”
-   25 - “data/procobj.dat”
-   26 - “data/maps”

### Using modified files

If you want to use modified data files from your GTA:SA install directory, check this check box:
Settings-&gt;Multiplayer-&gt;Use customized GTA:SA files (check box only appears if your GTA:SA data files are customized)
Note that this will restrict your access to public servers as most do not allow customized data files.

AC Panel resource
=================

An anti-cheat helper resource called **acpanel** is included with the default resources.

It shows the current anti-cheat status of your server, along with an option to keep your clients up to date and a basic implementation of [onPlayerModInfo](/docs/onplayermodinfo.md "wikilink") to block modified img files.

[Category: Support](/docs/category:_support.md "wikilink") [ru:Anti-cheat guide](/ru:Anti-cheat_guide.md "wikilink")
