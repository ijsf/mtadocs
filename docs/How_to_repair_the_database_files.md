You might be OK
---------------

There might be nothing to worry about. Check these points:

-   Did you come to this page because of a message you saw in the server console or logs?
-   Is the following text at the start of the error message block?

`   ERROR: near `“`3`”`: syntax error`

-   If so, then everything is OK. You don't have to do anything written below and you can safely ignore the error message.

Warnings
--------

**Backup all files before attempting a repair!**
**Shutdown the server before attempting a repair!**

Windows server
--------------

### Easy way

-   Download [this](http://updatesa.mtasa.com/sa/files/sqlite/mtasa-db-repair-win.zip)
-   Unzip and put the files into *server/mods/deathmatch/*
-   Double click on *sqlite\_repair\_internal\_db.bat* to repair internal.db
-   Double click on *sqlite\_repair\_registry\_db.bat* to repair registry.db

### Hard way

-   Download sqlite-shell-win32 from [here](http://www.sqlite.org/sqlite-shell-win32-x86-3070700.zip). If that link fails, the main download page is [here](http://www.sqlite.org/download.html).
-   Unzip and put sqlite3.exe into *server/mods/deathmatch/*
-   Open command prompt the change directory to *server/mods/deathmatch/*
-   To repair internal.db:
    -   Copy **internal.db** to **internal\_original.db**
    -   Do this command: **sqlite3.exe internal\_original.db .dump | sqlite3.exe internal\_repaired.db**
    -   Copy **internal\_repaired.db** to **internal.db**

<!-- -->

-   To repair registry.db:
    -   Copy **registry.db** to **registry\_original.db**
    -   Do this command: **sqlite3.exe registry\_original.db .dump | sqlite3.exe registry\_repaired.db**
    -   Copy **registry\_repaired.db** to **registry.db**

Linux server
------------

### Only way

(You can use the easy way by copying the DB from linux to windows, and use the method used on windows PC's)

-   Download sqlite-shell-linux from [here](http://www.sqlite.org/sqlite-shell-linux-x86-3070700.zip). If that link fails, the main download page is [here](http://www.sqlite.org/download.html).
-   Unzip and put sqlite3 into *server/mods/deathmatch/*
-   To repair internal.db:
    -   Copy **internal.db** to **internal\_original.db**
    -   Do this command: **./sqlite3 internal\_original.db .dump | ./sqlite3 internal\_repaired.db**
    -   Copy **internal\_repaired.db** to **internal.db**

<section name="Commands" class="server" show="false">
    cp internal.db internal_original.db
    ./sqlite3 internal_original.db .dump | ./sqlite3 internal_repaired.db
    cp internal_repaired.db internal.db

</section>
-   To repair registry.db:
    -   Copy **registry.db** to **registry\_original.db**
    -   Do this command: **./sqlite3 registry\_original.db .dump | ./sqlite3 registry\_repaired.db**
    -   Copy **registry\_repaired.db** to **registry.db**

<section name="Commands" class="server" show="false">
    cp registry.db registry_original.db
    ./sqlite3 registry_original.db .dump | ./sqlite3 registry_repaired.db
    cp registry_repaired.db registry.db

</section>
[Category: Support](/docs/Category:_Support.md "wikilink") [ru:How to repair the database files](/ru:How_to_repair_the_database_files.md "wikilink")
