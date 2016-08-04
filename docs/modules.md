Modules are extensions for Multi Theft Auto's Lua core, allowing the integration and use of custom Lua functions that have been written in C++, and compiled as a DLL or SO file. Modules are commonly used to create functions for such purposes that Multi Theft Auto lacks, such as sockets. All modules listed here are not distributed with Multi Theft Auto, and must be manually installed.

Modules list
------------

You can view a list of all the documented modules in this wiki [here](/docs/:category:modules.md "wikilink").

Modules SDK
-----------

To be able to create your own modules, you must use the Modules SDK. You can download it from one of the links below - choose a link in accordance with your server's operating system.

-   Linux
    -   [Official](http://files.mtasa.com/apps/1.0/dm/ml_devkit.tar.gz)
        -   (Delete the .d files, and add \#include <cstring> to Common.h)
            -   (On 64bit add -m32 to CPPFLAGS and LDFLAGS lines in Makefile)
-   Microsoft Windows
    -   [Mirror (Mediafire)](http://www.mediafire.com/?b8b3asgegn0xkm4)
    -   [Mirror (MEGA)](https://mega.co.nz/#!nBNGUCgQ!3AHEJt684Heu9bN5de8xwAQ3h-qq5-V6fjUeU7rj5hI)

### SDK Functions

-   Currently in there:
    -   Base:
        -   HelloWorld
    -   MySQL
        -   MySQLCreate
        -   MySQLOpen
        -   MySQLDestroy
        -   MySQLQuery
        -   MySQLSafeString

[Category:Scripting Concepts](/docs/category:scripting_concepts.md "wikilink") [Category:Incomplete](/Category:Incomplete.md "wikilink") [Category:Modules](/Category:Modules.md "wikilink")

[pl:Modules](/docs/pl:modules.md "wikilink") [pt-br:Módulos](/pt-br:Módulos.md "wikilink") [ru:Modules](/ru:Modules.md "wikilink")
