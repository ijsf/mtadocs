Texturizer is a module which provides TXD libary writing and GD functions to MTASA server. It is currently available Windows only, however since the build system is CMake it should be pretty simple to use it on another platforms.

Installation
------------

### Windows

1.  Uncompress the file Texturizer.dll into your *%PROGRAMFILES%\\MTA San Andreas\\server\\mods\\deathmatch\\modules\\* directory.
2.  Uncompress the GD libary binary bgd.dll and libpng14.dll into your *%PROGRAMFILES%\\MTA San Andreas\\server\\* directory.
3.  Then, add the following line in mtaserver.conf:

``` xml
  <module src="Texturizer.dll" />
```

Now all you have to do is start your server.

**Also Recommended:**

1.  Uncompress the texturizer resource to your *%PROGRAMFILES%\\MTA San Andreas\\server\\mods\\deathmatch\\resources\\* directory.
2.  Then, add the following line in mtaserver.conf:

``` xml
  <resource src="texturizer" startup="1" protected="0" />
```

This provides automatic memory cleanup when you forget to destroy images some resource used on it's unload.

Functions
---------

[Category:Modules](/Category:Modules.md "wikilink")

[ru:Modules/Texturizer](/ru:Modules/Texturizer.md "wikilink")
