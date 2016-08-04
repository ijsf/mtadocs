Preparing your system
---------------------

In order to build the Multi Theft Auto dedicated server, you will have to set up your system with the correct libraries and tools. In order to get these, you will have to install the latest [MacPorts release.](http://www.macports.org/)

Our network module is distributed as a precompiled binary library. The latest version for Mac OS X can be downloaded from our [Downloads page](http://mtasa-blue.google.com) on Google Code.

Setting up MacPorts
-------------------

Since our software relies on a number of well known libraries that are not shipped on a vanilla Mac OS X system, it may be necessary for you to install these first. With the MacPorts software you can easily download and install these libraries, so follow the [installation instructions](http://www.macports.org/install.php) at macports.org.

After installing MacPorts, you should install the following packages:

-   pcre
-   zlib
-   sparsehash
-   curl

To install these packages, use the **port install <package>** command in your Terminal application. If you are not running as root, you will have to use **sudo** in front.

Compiling the server
--------------------

MacPorts installs itself into **/opt/local** by default, so we will have to pass the appropriate compiler and linker search path flags to the configure command.

    autoreconf -fi
    CPPFLAGS="-I/opt/local/include" LDFLAGS="-L/opt/local/lib" ./configure
    make install

Your vanilla server will now be compiled and installed into the **MTA10\_Server/output/** directory.

Run the server
--------------

Grab the latest **net.so** from the Downloads page on GitHub and place it in your output directory, install the **accounts.xml**, **mtaserver.conf** and **acl.xml** files into the **mods/deathmatch/** directory and grab the latest resources from the [multitheftauto-resources project](http://code.google.com/p/mtasa-resources/). You can then run your server.

    cd MTA10_Server/output
    ./mta-server

[ru:Building MTASA Server on Mac OS X](/docs/ru:building_mtasa_server_on_mac_os_x.md "wikilink") [Category: Development](/Category:_Development.md "wikilink")
