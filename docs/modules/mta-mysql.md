<pageclass class="#AA7592" subcaption="MTA-MySQL Module"></pageclass> MTA MySQL is an alternative to the default [ml\_mysql](/docs/modules/mysql.md "wikilink") module provided by the MTA team. It is available for Windows and GNU/Linux and provides the source code.

*Note: From version 0.4 it supports both DP2.3 and 1.0 servers.*

Installation
------------

### Windows

Uncompress the file mta\_mysql.dll into your *C:\\Program files\\MTA San Andreas\\server\\mods\\deathmatch\\modules\\* directory and the file libmysql.dll into your *C:\\Program files\\MTA San Andreas\\server\\* directory.

Then, add the following line in mtaserver.conf:

``` xml
  <module src="mta_mysql.dll" />
```

### GNU/Linux

32 bit copy mta\_mysql.so into the *mods/deathmatch/modules/* directory.
64 bit copy mta\_mysql.so into the *x64/modules/* directory.

Then, add the following line in mtaserver.conf:

``` xml
  <module src="mta_mysql.so" />
```

To fix **MODULE: Unable to find modules/mta\_mysql.so (libmysqlclient.so.15: cannot open shared object file: No such file or directory)!** you have to install libmysqlclient15. You can get it here: <http://automation.binarysage.net/?p=1311>

**If you experience an error on Unix systems:** Try to add port and socket parameters to your mysql\_connect.

Handler functions
-----------------

Result managing functions
-------------------------

Version 0.5 calling method
--------------------------

From version 0.5 onwards you can call all this module functions, except mysql\_connect and mysql\_null, as if they are methods of an object.

For example, having a valid MySQL handler, you can do handler:query ( “SELECT \* FROM table” ) instead of mysql\_query ( handler, “SELECT \* FROM table” ).

### Function aliases

A function alias is a second name for a function, which makes calling any of the original name or the alias have the same result. The new aliases introduced in version 0.5 are:

-   result:num\_rows() is the same as result:numrows()
-   result:num\_fields() is the same as result:numfields()
-   result:free\_result() is the same as result:free()

[Category:Modules](/docs/category:modules.md "wikilink")

[ru:Modules/MTA-MySQL](/docs/ru:modules/mta-mysql.md "wikilink")
