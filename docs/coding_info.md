Introduction
------------

This page has information which would be useful for anyone who is doing coding for MTA SA. [Coding guidelines](/docs/coding_guidelines.md "wikilink") also has a lot of useful info.

Projects explained
------------------

-   Client - Core: Typically UI elements like main menu etc and isn't ever unloaded.
-   Client - Deathmatch: Where MTA makes all it's functions and events do stuff.
-   Client - Game SA: Low level stuff which is mainly function calls to the game so each element will have a game\_sa class like Vehicle, Ped, Object etc.
-   Client - GUI: It's just wrappers to CEGUI, you need not touch.
-   Client - Launch: Is the MTA executable which loads loader, you need not touch.
-   Client - Loader: You need not touch the loader either.
-   Client - Multiplayer SA: Hooks, code modification and that sort of low level things that lets us work.
-   Server - Core: Cazomino05: “I genuinely don't really know why we have server core.”
-   Server - Dbconmy: Stuff to do with the db\* functions, you need not touch.
-   Server - Deathmatch: All the server logic and storage classes for elements as well as Lua stuff.
-   Server - Launcher: Just an executable to load all the DLLs we need.
-   Shared - XML Module: XML module is just tinyxml and some high level wrapper functions for stuff we need.
-   Dependencies: Has a load of 3rd party code, modules like sqlite, curl, lua, ehs, etc.
-   CEGUI: Crazy Eddie's GUI system is a graphical user interface C++ library.

Some of the code may be explained in detail in pages under the this category: [Classes (Blue)](/docs/-category-classes_(blue).md "wikilink")

Simplification of data types
----------------------------

MTA has some type definitions you can use (Can be found in Shared/sdk/SharedUtil.h)

-   ulong = unsigned long
-   uint = unsigned int
-   ushort = unsigned short
-   uchar = unsigned char
-   uint64 = unsigned long long
-   uint32 = unsigned int
-   uint16 = unsigned short
-   uint8 = unsigned char
-   int64 = signed long long
-   int32 = signed int
-   int16 = signed short
-   int8 = signed char
-   BYTE = unsigned char
-   WORD = unsigned short
-   DWORD = unsigned long
-   FLOAT = float

Debug Commands
--------------

MTA has some commands which you can use if you're running debug mode

-   showsync - show sync data
-   foo - debug command for devs
-   showwepdata - shows the given player weapon data (nick)
-   showtasks - shows the local player tasks (nick)
-   showplayer - shows extended player information (nick)
-   setmimic - enables player mimics (amount)
-   setmimiclag - enables player mimic lag (amount)
-   paintballs - enables paintball mode
-   breakpoint - inserts breakpoint
-   giveweapon - gives the player a weapon (id)
-   showrpcs - shows the remote prodecure calls
-   showinterpolation - shows information about the interpolation
-   watch - enables wpm watch mode
-   modules - enables wpm module
-   debug - debug function 1
-   debug2 - debug function 2
-   debug3 - debug function 3
-   debug4 - debug function 4

Entity types
------------

-   CCLIENTCAMERA - Camera
-   CCLIENTPLAYER - Player
-   CCLIENTVEHICLE - Vehicle
-   CCLIENTRADARMARKER - Blip
-   CCLIENTOBJECT - Object
-   CCLIENTPICKUP - Pickup
-   CCLIENTRADARAREA - RadarArea
-   CCLIENTMARKER - Marker
-   CCLIENTTEAM - Team
-   CCLIENTPED - Ped
-   CCLIENTPROJECTILE - Projectile
-   CCLIENTGUI:
-   CGUI\_BUTTON - GuiButton
-   CGUI\_CHECKBOX - GuiCheckBox
-   CGUI\_EDIT - GuiEdit
-   CGUI\_GRIDLIST - GuiGridList
-   CGUI\_LABEL - GuiLabel
-   CGUI\_MEMO - GuiMemo
-   CGUI\_PROGRESSBAR - GuiProgressBar
-   CGUI\_RADIOBUTTON - GuiRadioButton
-   CGUI\_STATICIMAGE - GuiStaticImage
-   CGUI\_TAB - GuiTab
-   CGUI\_TABPANEL - GuiTabPanel
-   CGUI\_WINDOW - GuiWindow
-   CGUI\_SCROLLPANE - GuiScrollPane
-   CGUI\_SCROLLBAR - GuiScrollBar
-   CGUI\_COMBOBOX - GuiComboBox
-   CCLIENTCOLSHAPE - ColShape
-   SCRIPTFILE - File
-   CCLIENTDFF - EngineDFF
-   CCLIENTCOL - EngineCOL
-   CCLIENTTXD - EngineTXD
-   CCLIENTSOUND - Sound
-   CCLIENTWATER - Water
-   CCLIENTDXFONT - DxFont
-   CCLIENTGUIFONT - GuiFont
-   CCLIENTTEXTURE - DxTexture
-   CCLIENTSHADER - DxShader
-   CCLIENTWEAPON - Weapon
-   CCLIENTEFFECT - Effect
-   CCLIENTSCREENSOURCE - DxScreenSource
-   CCLIENTRENDERTARGET - DxRenderTarget

[Category: Development](/docs/category-_development.md "wikilink")
