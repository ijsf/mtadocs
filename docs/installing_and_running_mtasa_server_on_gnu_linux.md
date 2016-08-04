Installation 64 bit
-------------------

### Main binary

Download the latest stable 64 bit Linux binaries:

`rm -f multitheftauto_linux_x64-``.tar.gz`
`wget http://linux.mtasa.com/dl/``/multitheftauto_linux_x64-``.tar.gz`

Unpack into a directory:

`tar -xf multitheftauto_linux_x64-``.tar.gz`

### Default config

Download the default config files:

`rm -f baseconfig-``.tar.gz`
`wget http://linux.mtasa.com/dl/``/baseconfig-``.tar.gz`

Unpack and move into the deathmatch directory:
(***Note:** Only do this for new installations as it will overwrite any existing config files.)*

`tar -xf baseconfig-``.tar.gz`
`mv baseconfig/* multitheftauto_linux_x64-``/mods/deathmatch`

Change to the MTA server install directory:

`cd multitheftauto_linux_x64-`

### Test

You can now test if the server will start correctly:

`./mta-server64`

### Default resources

If you need the default resources: Download the latest default resources zip from <http://mirror.mtasa.com/mtasa/resources/> and unzip into **mods/deathmatch/resources**
**Make sure you are in the MTA server install directory when following this example:**

`apt-get install unzip`
`mkdir mods/deathmatch/resources`
`cd mods/deathmatch/resources`
`rm -f mtasa-resources-latest.zip`
`wget http://mirror.mtasa.com/mtasa/resources/mtasa-resources-latest.zip`
`unzip mtasa-resources-latest.zip`
`rm -f mtasa-resources-latest.zip`
`cd ../../..`

Installation 32 bit
-------------------

### Main binary

Download the latest stable 32 bit Linux binaries:

`rm -f multitheftauto_linux-``.tar.gz`
`wget http://linux.mtasa.com/dl/``/multitheftauto_linux-``.tar.gz`

Unpack into a directory:

`tar -xf multitheftauto_linux-``.tar.gz`

### Default config

Download the default config files:

`rm -f baseconfig-``.tar.gz`
`wget http://linux.mtasa.com/dl/``/baseconfig-``.tar.gz`

Unpack and move into the deathmatch directory:
(***Note:** Only do this for new installations as it will overwrite any existing config files.)*

`tar -xf baseconfig-``.tar.gz`
`mv baseconfig/* multitheftauto_linux-``/mods/deathmatch`

Change to the MTA server install directory:

`cd multitheftauto_linux-`

### Test

You can now test if the server will start correctly:

`./mta-server`

### Default resources

If you need the default resources: Download the latest default resources zip from <http://mirror.mtasa.com/mtasa/resources/> and unzip into **mods/deathmatch/resources**
**Make sure you are in the MTA server install directory when following this example:**

`apt-get install unzip`
`mkdir mods/deathmatch/resources`
`cd mods/deathmatch/resources`
`rm -f mtasa-resources-latest.zip`
`wget http://mirror.mtasa.com/mtasa/resources/mtasa-resources-latest.zip`
`unzip mtasa-resources-latest.zip`
`rm -f mtasa-resources-latest.zip`
`cd ../../..`

Running with 32 or 64 bit Linux
-------------------------------

### Make sure your server libraries and stuff are up to date

On Debian/Ubuntu this is done with:

`apt-get update`
`apt-get upgrade`

### Troubleshooting

-   If you get a problem with such as “libreadline.so.5: cannot open shared object file: No such file or directory.”, it can be solved on 32 bit Debian/Ubuntu by doing this:

`apt-get install libreadline5`

-   If you get a problem with such as “libncursesw.so.5 cannot open shared object file: No such file or directory”, it can be solved on 32 bit Debian/Ubuntu by doing this:

`apt-get install libncursesw5`

**Note:** If you experience this issue on a 64-bit machine while trying to run the 32-bit MTA server, then you should install the following package on a 64-bit Debian/Ubuntu machine (as root):

`apt-get install lib32ncursesw5`

You can find more 32-bit library alternatives on this page: [www.debian.org/distrib/packages\#search\_contents](http://www.debian.org/distrib/packages#search_contents).

MySQL Troubleshooting
---------------------

-   If you are using the inbuilt MySQL functions such as [dbConnect](/docs/dbConnect.md "wikilink") and [dbQuery](/dbQuery.md "wikilink"), you will need to have **libmysqlclient.so.16** installed.
-   If you get a problem with such as “libmysqlclient.so.16: cannot open shared object file: No such file or directory”, it can be solved on Debian/Ubuntu by doing this:

`apt-get install libmysqlclient16`

If that fails:

-   For 32 bit Linux, download [32 bit libmysqlclient.so.16](http://nightly.mtasa.com/files/modules/32/libmysqlclient.so.16) and put it in **/usr/lib/**
-   For 64 bit Linux, download [64 bit libmysqlclient.so.16](http://nightly.mtasa.com/files/modules/64/libmysqlclient.so.16) and put it in **/usr/lib/**

\[Optional\] Installing and Configuring an External Web Server
--------------------------------------------------------------

Instructions on how to install and configure Nginx as an external web server for MTA is here: [Installing and Configuring Nginx as an External Web Server](/docs/Installing_and_Configuring_Nginx_as_an_External_Web_Server.md "wikilink")

Server crashes
--------------

If your Linux server crashes, please obtain a backtrace and post a report on our [Bug tracker](http://bugs.mtasa.com/)

#### To obtain a backtrace:

### Do you have a core dump file in the the MTA server directory?

It's usually called 'core', and usually over 100MB, and looks something like this:

[`Image:Core.png`](/docs/Image:Core.png.md "wikilink")

#### If you have a core dump file in the the MTA server directory:

-   Install gdb. To install gdb on Debian, use this command:

`apt-get install gdb`

-   And from the MTA install directory do this command

`gdb mta-server -c core`

-   When gdb launches, do this command to get a module list:

`i sh`

-   And then this command to get a backtrace:

`bt`

-   Save the output
-   (To exit gdb, use the quit command)

#### If you do not have a core dump file in the the MTA server directory:

-   Install gdb. To install gdb on Debian, use this command:

`apt-get install gdb`

-   And from the MTA server directory start the mta-server like this:

`gdb mta-server -ex `“`set` `print` `thread-events` `off`”` --eval-command run`

-   Now wait for a crash. (Ignore any weird screen output in the meantime)
-   When a crash occurs, do this command to get a module list:

`i sh`

-   And then this command to get a backtrace:

`bt`

-   Save the output
-   (To exit gdb, use the quit command)

**Server freezes**
------------------

If your Linux server freezes, please obtain a backtrace with thread information and post a report on our [Bug tracker](http://bugs.mtasa.com/)

#### To obtain a backtrace with thread information:

-   Install gdb. To install gdb on Debian, use this command:

`apt-get install gdb`

-   And from the MTA server directory start the mta-server like this:

`gdb mta-server -ex `“`set` `print` `thread-events` `off`”` --eval-command run`

-   Now wait for a freeze. (Ignore any weird screen output in the meantime)
-   When a freeze occurs, press ctrl-c to start gdb
-   Then do this command to get a module list:

`i sh`

-   And then this command to get a backtrace:

`bt`

-   And then this command to get thread information:

`info threads`

-   Save the output
-   (To exit gdb, use the quit command)
