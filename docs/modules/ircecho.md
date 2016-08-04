MTASA IRC Echo is a module that provides an IRC echo for an MTASA server. It is available for both Windows and Linux.

Installation
------------

### Windows

Uncompress the file ml\_ircecho.dll into your *%PROGRAMFILES%\\MTA San Andreas\\server\\mods\\deathmatch\\modules\\* directory.

Then, add the following line in mtaserver.conf:

``` xml
  <module src="ml_ircecho.dll" />
```

### Linux

Uncompress the file ml\_ircecho.so into your *%MTASERVER%\\mods\\deathmatch\\modules\\* directory.

Then, add the following line in mtaserver.conf:

``` xml
  <module src="ml_ircecho.so" />
```

Functions
---------

Callbacks
---------

[ru:Modules/IRCEcho](/docs/ru:Modules/IRCEcho.md "wikilink")
