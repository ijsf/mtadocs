This is hashing string module. It uses 2 algorithms of hashing. One is alder32 (which is not actually the real alder32 algorithm, I do not recommend using it) and one is MD5. Using MD5 you get 32-characters long hexadecimal number.

CURRENTLY IT'S ONLY FOR WINDOWS SERVERS.

Installation
------------

### Windows

**\* Important \***

This module was compiled in Visual C++ 2008, as such it requires Visual C++ 2008 or the Visual C++ 2008 runtime libraries which are considerably smaller. You can get this ~1.8MB Installation package [Here](http://www.microsoft.com/downloads/details.aspx?familyid=9B2DA534-3E03-4391-8A4D-074B9F2BC1BF&displaylang=en).

Uncompress the file hashing.dll into your *C:\\Program Files\\MTA San Andreas\\server\\mods\\deathmatch\\modules\\* directory.

Then, add the following line in mtaserver.conf:

``` xml
  <module file="hashing.dll" />
```

Functions
---------

[Category:Modules](/docs/category:modules.md "wikilink")

[ru:Modules/hashing](/docs/ru:modules/hashing.md "wikilink")
