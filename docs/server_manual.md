Getting started
---------------

It is much easier than it looks to get a server up and running for your internet or LAN buddies; follow this wiki article and you will hopefully be on your way to hosting your own MTA:SA server in no time!

Installing the server
---------------------

The dedicated server application is available in different flavours depending on the platform of the server.

### Linux installation

There are different ways of getting a Linux server up and running:

-   [Getting a precompiled package](http://linux.mtasa.com)
-   [Installing and Running MTASA Server on GNU Linux](/docs/installing_and_running_mtasa_server_on_gnu_linux.md "wikilink")
-   [Building MTASA Server on GNU Linux](/docs/building_mtasa_server_on_gnu_linux.md "wikilink")

Should you have any problems with errors when starting the server some common problems and solutions are listed here:

-   [Building MTASA Server on GNU Linux\#Troubleshooting](/docs/building_mtasa_server_on_gnu_linux#troubleshooting.md "wikilink")

### FreeBSD installation

You can run MTA:SA under FreeBSD using Linux emulation.

-   Enable [Linux binary compatibility](http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/linuxemu-lbc-install.html)
-   Install following packages or compile them from ports: hs-terminfo, linux\_base-f10, linux-f10-sqlite3
-   Install [Linux precompiled package](http://linux.mtasa.com/)

### Windows installation

Installation of the MTA:SA server on Windows is easy as pie.

-   Go to the [download page](http://mtasa.com/) and download the installer.
-   Once the installer is downloaded, open it.
-   Select a folder where you want to install the server.
-   Click Install.
-   Done!

*For a full explanation of acl.xml (access control list) read: [Access Control List](/docs/access_control_list.md "wikilink")*

Configuring your server
-----------------------

The Multi Theft Auto dedicated server is initially configurable through it's console window, from within the game, and from a webbrowser. In order to make use of the two last options, it is necessary to add at least one administrator user to your configuration file.

### General configuration

All general configuration options can be found in the 'mods/deathmatch/[**mtaserver.conf**](/docs/server_mtaserver.conf.md "wikilink")' file and can be opened by any regular text editor.

This file is fairly straightforward; every variable has a [description of what to do with it and how to change it](/docs/server_mtaserver.conf.md "wikilink").

### Port forwarding

If you run your server on your own private computer, and you have an router between the internet and your computer. You need to forward 3 ports.

First of all open the file 'mods/deathmatch/[**mtaserver.conf**](/docs/server_mtaserver.conf.md "wikilink")' and search for the next lines:

``` xml
<serverport>22003</serverport> 
<httpport>22005</httpport>
```

The ports are needed to setup the server correctly. We explain later how to set them, but first if you want your server to appear in the server browser there is another port we need, and that is the ASE port. (quick example for how to turn ASE on or off):

``` xml
<ase>1</ase> <!-- 0 = off, 1 = on -->
```

Now we going to forward the ports in your router, which is not needed if you already have all ports open, or if you don't have a router with a firewall. If so, skip this part.

If you don't know how port forwarding works in your router, go to the [Port Forward website](http://portforward.com/), find your router model there, and follow the instructions there.

In almost every router you can set the port type: UDP or TCP. The following list will explain which port type is needed for what:

Main server port: UDP

HTTP Port: TCP

ASE Port: UDP (this is needed if you want your server to appear in the server list)

The ASE port is also simple to get:

ASE port = Main server port + 123

So, if you have the main server port set to 22003, then the ASE port will be 22126.

Good luck!

*In the latest version of the server, you can check the port status by using the server command [openports](/docs/server_commands#openports.md "wikilink").*

### Client Checks

The MTA server can be configured to disable the anti-cheat. It can also allow specific or all files to be modified (e.g. carmods.dat), and make sure clients are of a minimum version.

All of these settings are within the file 'mods/deathmatch/[**mtaserver.conf**](/docs/server_mtaserver.conf.md "wikilink")'. See the [Anti-cheat guide](/docs/anti-cheat_guide.md "wikilink") for more details.
If you want to force a minimum client version, search for the following line:

``` xml
<minclientversion></minclientversion>
```

Accepted values look like: 1.1.1-9.02320

### Adding administrators

It is strongly recommended to add at least one administrator to your server in order to make use of the built-in webserver to easily maintain and configure your server. This administrator will then also be able to log-in from within the game and control the server.

To add an administrator to your server, follow these steps:

1.  While the server is running, add a new account by typing **[addaccount name password](/docs/server_commands#addaccount.md "wikilink")** into the server window. For example, to add user BennyLava you could type:
    <div style="margin: 10px 10px 10px 10px;">
    ``` xml
    addaccount BennyLava 123password
    ```

    </div>
    <div style="margin: 10px 10px 10px 20px;">
    *Note: If you do not have access to the server window, and the 'admin' resource is running, you can add the example account by issuing the client console (F8) command **register BennyLava 123password***

    </div>
2.  The server should display a message confirming the account has been added.
3.  Next, shutdown the server by typing **shutdown** into the server window.
4.  Make sure your server is stopped; if your server is still running, the following changes you make will be overwritten
5.  Open the file 'mods/deathmatch/acl.xml' with any text editor
6.  Add the account to the *Admin* group by using the XML-syntax below
    <div style="padding: 10px">
    ``` xml
    <acl>
      ...
      <group name="Admin">
        <acl name="Admin"/>
        ...
        <object name="user.BennyLava" />
      </group>
      ...
    </acl>
    ```

    </div>
    You're done! You can add as many administrators or users as you want this way, take a look at some of the other groups and ACLs for example. The ACL is also accessible through the [Lua scripting engine](/docs/access_control_list.md "wikilink").
    It is recommended to take a look at the web interface, we will explain how to do this below.

**Note**: There are also ways to add accounts and edit rights for the server while it's running. "[addaccount <user> <password>](/docs/server_commands#addaccount.md "wikilink")" is an internal command to add accounts, but you will have to use the web interface to add these accounts to specific groups/ACLs!

### Using the web interface

The dedicated server comes with a few Lua [resources](/docs/resources.md "wikilink") that provide a nice little web interface to your server. This can be used to easily maintain your server, as it allows you to add users, start/stop resources, and more.

The web interface resources are enabled by default and are served through the built-in HTTP web server. To make sure the built-in HTTP web server runs on a port you like (22005 by default), follow these steps:

1.  Make sure your server is stopped
2.  Open the file 'mods/deathmatch/[**mtaserver.conf**](/docs/server_mtaserver.conf.md "wikilink")' with any text editor
3.  Verify that the HTTP server is enabled:
    <div style="padding: 10px">
    ``` xml
        <httpserver>1</httpserver>
    ```

    </div>
4.  Change the HTTP server port to your liking:
    <div style="padding: 10px">
    ``` xml
        <httpport>22005</httpport>
    ```

    </div>
5.  Save and close the configuration file
6.  Start your server
7.  If you happened to have changed the start-up resources in your configuration file, make sure the following resources are started:
    1.  resourcebrowser
    2.  resourcemanager
    3.  webadmin
    4.  webmap

    These are automatically started in the default configuration file, in case you just installed your server.

8.  Open a web browser (Internet Explorer 6 or 7 are NOT supported; use [Mozilla Firefox](http://www.mozilla.com/firefox), [Google Chrome](http://www.google.com/chrome), [Apple Safari](http://www.apple.com/safari/download), [Opera](http://www.opera.com) or others) and navigate to the HTTP server URL: **[http://server:port/](http://server:port/)**. For example, If you are running a local server on HTTP port 22005, use **<http://127.0.0.1:22005/>**.
9.  Enter the username and password of the administrator you added in the previous section.

You should now be able to maintain your server from the web interface.

### Configuring an external web server

The built-in web server is also used to serve files that are required by resources running on your server to any player that is connected to your server. For example, if you are running a game script with a scripted graphical user interface, or custom models, these need to be transferred to every connected player in order to function properly. This is done by either the built-in web server, or an external web server (that is usually a bit faster) but needs to be set up separately.

For performance or consistency reasons during the game, you could choose to make use of such an external web server if you have one set up. The external web server needs to be accessible for the public, so any client will be able to download the necessary client-side files in order to join and play on your server.

To enable downloading off an external web server, you should configure the [httpdownloadurl](/docs/server_mtaserver.conf#httpdownloadurl.md "wikilink") tag in your server configuration:

<div style="padding: 10px">
``` xml
    
<httpdownloadurl>http://www.myserver.tld/directory/here</httpdownloadurl>
```

</div>
When you launch the server, the directory **<SERVER>/mods/deathmatch/resource-cache/http-client-files** will contain the correct client files for hosting on an external web server. If the web server is on the same machine, you can simply link the appropriate web server directory to **http-client-files**. If the web server is on a separate machine, ensure it has access to **http-client-files** via a network path, or maintain a remote copy using synchronization software.

**Note 1**: Please try to avoid any special characters (e.g. ~, !) in your download URLs.
**Note 2**: Please do not use a trailing slash in your download URL (e.g. *http://www.myserver.tld/directory* rather than *http://www.myserver.tld/directory/*)
**Note 3**: The web server must use 'ContentType: application/octet-stream' for Lua files. Most web servers will do this by default, or you can add the following line to the .htaccess file:

<div style="padding: 10px">
``` xml
AddType application/octet-stream .lua
```

</div>
Instructions on how to install and configure Nginx as an external web server for MTA is here: [Installing and Configuring Nginx as an External Web Server](/docs/installing_and_configuring_nginx_as_an_external_web_server.md "wikilink")

Starting your server
--------------------

Begin by making sure that you have finished all configuration of your server, starting your server is the last stage so everything must be ready!

To start your server double click on MTA Server.exe, make sure you allow it through any firewalls and forward ports where necessary.

Installing/Updating resources on your server
--------------------------------------------

Resources can come in two formats, either a ZIP format or just a normal folder with the script files inside it. The MTA:SA server supports both these methods.

1.  Move or copy the new resource to your <SERVER>\\mods\\deathmatch\\resources folder.
2.  In the server window type in the command [refresh](/docs/server_commands#refresh.md "wikilink"), this will re-scan the resources folder and update the live resources where necessary.

Uninstalling resources
----------------------

Resources can easily be removed from your server if you no longer want them.

1.  Delete the ZIP file or the folder of the resource you wish to uninstall
2.  In the server window type in the command “refresh” (without the quotes), this will re-scan the resources folder and update the live resources where necessary.

Administrating your server
--------------------------

You can start resources by typing the command “start resourcename” in the server console, or stop ones with “stop resourcename”.

It's also possible to execute these and other admin commands from the in-game console (which you can bring up with the \` key or F8); for this to work, you first need to log in with the command "[login username password](/docs/server_commands#login.md "wikilink")". Additionally, you can press the p key to bring up the admin panel: this is a graphical interface which allows you to easily kick or ban misbehaving players, among others.

For further commands, type [help](/docs/server_commands#help.md "wikilink") in a console.

Starting a map/gamemode
-----------------------

See the commands section of the documentation for [mapmanager](/docs/resource:map_manager.md "wikilink") for more information.

Useful Notes
------------

1.  You may also update the resources while in-game as long as you have the correct access levels by typing “refresh” in the clients console or "/refresh" in the chat window. This may cause a second of lag if you have many resources.
2.  In the above instructions, <SERVER> is the path to your server's main directory. In most cases this is C:\\Program Files\\MTA San Andreas\\server
3.  You can choose a different config file for the server to use by passing it in the command line after a --config argument, e.g. mtaserver.exe --config anotherconfig.cfg.
4.  Do not be alarmed by the warning regarding the parsing of the settings.xml file. This happens because your server installation is still clean and unused.

#### Need further help?

Why not pop over to our [Forums](http://forum.mtasa.com/) or join us on [IRC](irc://irc.multitheftauto.com/mta) (irc.multitheftauto.com \#mta - [mIRC](http://www.mirc.com))

[es:Manual del Servidor](/docs/es:manual_del_servidor.md "wikilink") [de:Server Anleitung](/docs/de:server_anleitung.md "wikilink") [it:Manuale del Server](/docs/it:manuale_del_server.md "wikilink") [nl:Server Manual](/docs/nl:server_manual.md "wikilink") [ru:Server Manual](/docs/ru:server_manual.md "wikilink") [pl:Server Manual](/docs/pl:server_manual.md "wikilink") [pt-br:Manual do Servidor](/docs/pt-br:manual_do_servidor.md "wikilink") [hu:Server Manual](/docs/hu:server_manual.md "wikilink")

[Category:Support](/docs/category:support.md "wikilink")
