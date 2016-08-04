In order to successfully build Multi Theft Auto from source, it is necessary to perform a number of steps, which we will explain below. You should be using Windows 7 or above to build.

### Prerequisites

Before you can build Multi Theft Auto, make sure you have the following software and SDKs installed:

-   Visual Studio **2013**
    -   **Recommended:** [Visual Studio **2013** Community](https://go.microsoft.com/fwlink/?LinkId=530250) (Free)
        -   **Offline Installer**: [vs2013.5.iso](https://go.microsoft.com/fwlink/?LinkId=519391) (5,96 GB)
    -   **Latest:** [Microsoft Visual Studio 2015](https://www.visualstudio.com/en-us/downloads/download-visual-studio-vs.aspx) (Community Edition is free).
-   [Microsoft DirectX SDK](http://www.microsoft.com/en-us/download/details.aspx?displaylang=en&id=6812)
    -   **S1023 Error:** [“S1023” error when you install the DirectX SDK (June 2010)](https://support.microsoft.com/en-us/kb/2728613)

If you haven't already done so, install a client such as [SourceTree](https://www.sourcetreeapp.com/) or [GitHub for Windows](https://windows.github.com/), which can be used to download and manage the code.

### Getting the latest source code

To get the latest code, you will have to download the latest copy of our Git repository - you can get it [here](https://github.com/multitheftauto/mtasa-blue) ([zip](https://github.com/multitheftauto/mtasa-blue/archive/master.zip)|[tar.gz](https://github.com/multitheftauto/mtasa-blue/archive/master.tar.gz))

### Before building the software

To ensure the target directories have the correct permissions it is **vital** to install \[<http://nightly.mtasa.com/?mtasa->-full\_unstable-latest the latest unstable nightly Windows full installer\] into this **exact** directory:

`   C:\Program Files\MTA San Andreas ``\`

If you have 64 bit windows, be sure to remove (x86) from the path.

### Building the software

In order to build the source, you will need Microsoft Visual Studio. Open the project file in **Shared/Core 2013.sln** and build using one of the project configurations *Debug* or *Release*. Note that everything will run significantly slower in *Debug* mode.

### Target directory and permissions

By default, the current version compiles the binaries into **C:\\Program Files\\MTA San Andreas \\**. To ensure the correct permissions, registry entries and support files are present, you should install \[<http://nightly.mtasa.com/?mtasa->-full\_unstable-latest the latest unstable nightly Windows full installer\] into that directory. Also make sure to add write permissions for your user to that directory.

### Getting the latest network module

Since the **netc.dll**/**net.dll** network modules for the client are covered by a different license, you will have to use the binary files that get installed with the latest nightly. If you want to run a debug version of MTA, MTA expects a debug version of the net dll. As we don't provide this, you can append '\_d' to the filename of a release dll.

Furthermore, it is advisable to create an empty “timeout.longtime” file in your MTA server/ directory. This will extend the time before players are kicked from your server for unresponsiveness to 120 seconds. This is useful when in Debug mode on the client and the process is halted.

Running the software
====================

You are almost ready to run your build of the Multi Theft Auto software.

### Running the game client

Double check you have installed \[<http://nightly.mtasa.com/?mtasa->-full\_unstable-latest the latest unstable nightly Windows full installer\].

### Running the dedicated server

If you want to run the Multi Theft Auto dedicated server, you will have to install the required resources. These are required because they implement the most basic functionality (e.g. spawning players) in order to play.

Our official resources repository is hosted on GitHub: [1](https://github.com/multitheftauto/mtasa-resources). It's recommended that you check out the latest resources from there or [download a zipped revision from here](http://mirror.mtasa.com/mtasa/resources/). Make sure that you are not using any of our resources from any previous versions of Multi Theft Auto, as this **will** cause issues.

If you have any problems with missing DLL files (e.g. libcurl.dll), then you didn't install the Windows full installer properly.

Getting involved
================

Please see our [Coding guidelines](/docs/coding_guidelines.md "wikilink") for information on coding practice.

Additional information
======================

If you need more information, try our [bug tracker](http://bugs.mtasa.com/), [IRC channel](irc://irc.multitheftauto.com).

[pt-br:Compilando o MTASA](/docs/pt-br:compilando_o_mtasa.md "wikilink") [ru:Compiling MTASA](/docs/ru:compiling_mtasa.md "wikilink") [Category: Development](/docs/category:_development.md "wikilink")
