Making MTA work with handling.cfg
=================================

MTA ignores the GTA file data/handling.cfg because of the custom handling functions.

There are two ways to get a custom handling.cfg working in MTA:

Easy way
--------

To load custom handling.cfg, follow these steps:

-   Download the [Handling Loader resource](http://nightly.mtasa.com/files/res/handling_loader.zip)
-   Unzip **handling\_loader.zip** contents into **server/mods/deathmatch/resources/handling\_loader/**
-   Start server, or type **refresh** into the server console
-   (Optional) Copy the global **handling.cfg** into **server/mods/deathmatch/resources/handling\_loader/**
-   (Optional) Tell clients to put their personalized **handling.cfg** into **MTA San Andreas 1.3\\mods\\deathmatch\\resources\\handling\_loader\\**
-   Start **Handling Loader** with the command **start handling\_loader**

The server handling.cfg will apply to everyone on the server. (If installed)
The customized handling lines of the player installed handling.cfg will only apply to the cars that player drives.

<span style="text-decoration: line-through;">Future way
-------------------------------------------------------

<span style="text-decoration: line-through;">To import a custom handling.cfg, follow these steps:

-   <span style="text-decoration: line-through;">Download the [Handling Editor resource](http://community.multitheftauto.com/index.php?p=resources&s=details&id=3716)
-   <span style="text-decoration: line-through;">Unzip **hedit.zip** into **server/mods/deathmatch/resources/hedit/**
-   <span style="text-decoration: line-through;">Start server, or type **refresh** into the server console
-   <span style="text-decoration: line-through;">Copy your **handling.cfg** into **server/mods/deathmatch/resources/hedit/**
-   <span style="text-decoration: line-through;">Start Handling Editor with the command **start hedit**
-   <span style="text-decoration: line-through;">Enter this command in the server console: **loadcfg**
-   <span style="text-decoration: line-through;">Oh, it's broken
-   <span style="text-decoration: line-through;">Contact the author
