<pageclass class="#62A033" subcaption="FileSystem module"></pageclass>

FileSystem is the [MTA:Eir](/docs/MTA:Eir.md "wikilink") file management implementation exported as MTA:BLUE module. It is made for those people who are not satisfied with the standard MTA file functions. Its feature-set covers **binary stream writing**, **directory scanning** and **path resolution logic**. It should satisfy all needs regarding file functionality. The modules' source code is released within the MTA:Eir SVN.

Its documentation can be found [here](/docs/MTA:Eir/FileSystem.md "wikilink"). To find coding examples, *browse the individual class methods*.

Installing FileSystem into your Server
--------------------------------------

-   Place the fileSystem\*.dll module into your MTA server modules directory
-   Add the module into the mtaserver.conf module loading list (at the bottom of the file)
-   **Edit the acl.xml in a way that resources require admin rights to call** [createFilesystemInterface](/docs/MTA:Eir/FileSystem/createFilesystemInterface.md "wikilink")''

System Access Possibilities
---------------------------

-   Accessing whole system
-   Listing and editing all server resources
-   Modifying MTA Server configuration

**Be careful how you expose the FileSystem module to your server resources!**

Support
-------

To ask questions about this module, report any bugs or just hang around in general, join \#mta.recore at irc.gtanet.com

-   [Porting Clientside and Serverside code](/docs/Modules/FileSystem/Porting_Between_Clientside_and_Serverside.md "wikilink")

**LINUX: The .so module currently has stability issues due to conflicting Lua versions. I am working on resolving these. Until then the module may crash when executing callbacks (namely scanDir or scanDirEx methods).**

[Category:Modules](/docs/Category:Modules.md "wikilink")
