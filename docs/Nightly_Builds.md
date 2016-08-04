Nightly builds are experimental builds and thus do not work straight out-of-the-box, as they exclude a few files that rarely change but are necessary to work. This is because of size and bandwidth issues, and the fact that they are meant as incremental updates for those that already have the necessary files installed.

Please bear in mind that these builds are developer builds and will be unstable. For a list of changes for each revision, head over to our [buildinfo page](https://buildinfo.mtasa.com) for a commit breakdown of each build.

Our automated build server takes care of building (and subsequently uploading) the latest commit. The integration build starts at certain intervals during the day to check for build errors while the nightly build is built at 23:00 (GMT/DST).

Setting up nightly builds
=========================

Nightly builds are designed in a manner in which minimal updates are required in order to install a new nightly. This however means that you \*must\* first follow some specific steps to get your nightly build working.

### Download the latest nightly build “full installer”

First off you should download the latest available nightly build. For Windows, two different installers are available: a nightly installer and a full installer.

-   Nightly installer: a minimal installer that excludes data files that rarely change and the resources package
-   Full installer: the full installer that includes the data files and resource package

These data files are dependencies that rarely need to be updated. If your build starts malfunctioning for any reason it may be because you need to update your dependencies. They are updated whenever needed. Just run the full installer and install it to the correct folder.

### Download the latest resources

The latest resources are also available, you probably don't need this when you're using the full installer. These components are only required if you wish to run a server or the map editor. Default resources from previous versions of MTASA are outdated, and will not function.

-   You should pick the resource archive with the **highest revision number**.
-   You can find the latest available resources **[here](https://mirror.mtasa.com/mtasa/resources/)**.
-   The contents of the archive should be placed inside your **MTA San Andreas\\server\\mods\\deathmatch\\resources** directory. You will need to create a resources directory if you do not already have one.

Resources should also be updated fairly frequently. They are built at 2300GMT, depending on changes that are made during that day. You should always ensure you always have the latest resourecs package.

### Optional: Download DirectX

You need DirectX (March 2009) installed. If you haven't updated DirectX since then, install [this](http://www.microsoft.com/downloads/details.aspx?FamilyId=2DA43D38-DB71-4C1B-BC6A-9B6652CD92A3&displaylang=en) - it only takes a minute or so.

### Step 4: Start the game

You have now installed all the components required to run a nightly build. You should now be able to run both the client and the server, or join any servers that may be available.

Bugs, suggestions or feedback can go in either our forums or the bugtracker

-   <https://forum.multitheftauto.com>
-   <https://bugs.multitheftauto.com>

For general scripting or server setup help, please refer to:

-   [Client Manual](/docs/Client_Manual.md "wikilink")
-   [Server Manual](/docs/Server_Manual.md "wikilink")
-   [Setting up admin on your server](/docs/admin.md "wikilink")
