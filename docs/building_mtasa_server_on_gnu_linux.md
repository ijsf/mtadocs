Installing and Running MTASA server on Linux
--------------------------------------------

Preparing your system
---------------------

In order to build the Multi Theft Auto dedicated server, you will have to set up your system with the correct libraries and tools. How these are installed depends on your distribution.

Our network module (net.dll or net.so) is distributed as a precompiled binary library. The file for GNU/Linux can be found inside the lastest Linux nightly from [here](http://nightly.mtasa.com/). Use the net.so from if you are compiling from the trunk, or the net.so from if you are compiling the branch. Be sure the read the top of *MTA10\_Server/version.h* as it contains directions on how to compile the different build types.

### Debian Linux

Includes derivative distributions such as Ubuntu.

You will need the necessary build tools, headers and libraries, which are distributed through the following Debian packages (e.g. Debian Lenny):

-   **build-essential:** contains the necessary tools, headers and libraries to build applications
-   **automake:** contains the automake tools
-   **libtool:** contains the libtool software required to build libraries

<!-- -->

-   **libreadline5-dev:** contains the readline library (version 5)
-   **libncurses5-dev:** contains software for controlling writing to the console screen
-   **libncursesw5-dev:** contains support for wide characters

<!-- -->

-   **libmysqlclient-dev:** contains the MySQL library
-   **git:** contains the git client used to check out our code repository

To install these packages through apt, use the apt-get install <package list> command as in the following example (execute as root):

`apt-get install build-essential automake libtool`
`apt-get install libreadline5-dev libncurses5-dev libncursesw5-dev`
`apt-get install libmysqlclient-dev git `

### Gentoo Linux

You will need the necessary build tools, headers and libraries. Because Gentoo’s portage system is designed to compile any packages on your own system, the necessary build tools will have already been installed. This only leaves you to install the necessary libraries:

-   **git:** contains the git client used to check out our code repository

To compile and install these packages through emerge, use the emerge -v <package list> command. The -v option shows additional \* \* information and can be omitted. (If you want to use any USE flags, prepend emerge with USE=“use flags here”. You can also use the -pv option to verify that you’re using the correct flags.) Refer to the [Gentoo Handbook](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=2&chap=1) or manual for more information on emerge.

Example:

`emerge -v git sqlite`
`USE=“net-misc/curl ssl” emerge -v curl`

### Fedora

You will need these packages to be able to successfully compile a MTA server on Fedora:

-   **glibc-devel:**

<!-- -->

-   **readline-devel:** contains the readline library

<!-- -->

-   **git:** contains the git client to check out the source code

To install these packages through yum, use the yum install <package list> command as in the following example (execute as root):

`yum install glibc-devel readline-devel git`

General instructions for 
-------------------------

**Downloading the source.**

First you need to download the source. Either clone as show below or [download a zip snapshot](https://github.com/multitheftauto/mtasa-blue/archive/master.zip)

`git clone https://github.com/multitheftauto/mtasa-blue.git mtasa-blue`
`cd mtasa-blue`

Then compile it thus:

`./mta-build.sh`

Then copy the built binaries and configuration files into MTA10\_Server/output by running this command:

`./mta-install.sh`

Get the net.so like this:

`wget http://nightly.mtasa.com/?multitheftauto_linux-``-unstable-latest -O multitheftauto_linux-``-latest.tar.gz`
`tar -xzf multitheftauto_linux-``-latest.tar.gz --transform 's:[^/]*:latest_nightly:'`
`mv latest_nightly/net.so MTA10_Server/output/`
`rm -rf latest_nightly multitheftauto_linux-``-latest.tar.gz`

Get resources:

`wget https://github.com/multitheftauto/mtasa-resources/archive/master.tar.gz`
`tar -xf master.tar.gz`
`mv mtasa-resources-master MTA10_Server/output/mods/deathmatch/resources`

And the server should be ready in MTA10\_Server/output

### **Troubleshooting**

Any errors during the compilation of json-c can be solved by calling autoreconf -fi from the json-c directory.

If you’re getting any unexpected errors while compiling, please check our [Bug tracker](http://bugs.mtasa.com/) or our [IRC channel](irc://irc.multitheftauto.com/)

[ru:Building MTASA Server on GNU Linux](/docs/ru-building_mtasa_server_on_gnu_linux.md "wikilink") [Category: Development](/docs/category-_development.md "wikilink")
