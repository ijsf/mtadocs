MTA Protocol Handler
--------------------

eAi created a program on December 16th 2003 which allows you to connect to an MTA server with a simple URL syntax:

    mta://127.0.0.1:2003
    mtavc://127.0.0.1:2003

The orginal forum thread can be found [here](http://forum.mtasa.com/viewtopic.php?t=5662).

As a addition to the orginal mtahandler.mrc that enables the protocols in mIRC, Aeron has updated the code to handle mtasa:// protocols. Make sure though you have the correct directory containing the relevant \*.exe's):

    // This is the code for the MTA Protocol Handler
    // (c) eAi 2003
    // eAi@planethalflife.com
    // If you remove this, links beginning with mta:// and mtavc:// will no longer work.
    // Thanks to JimmyK for this code
    // Optimized and 'mtasa://' protocol handler by Aeron

    on ^*:hotlink:mtasa*//*:*: { !return } 
    on *:hotlink:mtasa*//*:*: { !run "C:\Program Files\MTA San Andreas\Multi Theft Auto.exe" $1 }

    on ^*:hotlink:mtavc*//*:*: { !return } 
    on *:hotlink:mtavc*//*:*: { !run "C:\Program Files\Multi Theft Auto\MTAPH" $1 }

    on ^*:hotlink:mta*//*:*: { !return } 
    on *:hotlink:mta*//*:*: { !run "C:\Program Files\Multi Theft Auto\MTAPH" $1 }

The URL syntax would be for the race mod:

    mtasa://race@127.0.0.1:2003

MTA:mA
------

MTA:mA is an mIRC based admin client that enables server owners to run mIRC scripts on their servers, amongst other things.

More details available [here](/docs/mta-ma.md "wikilink").

MTA Stop Watch
--------------

This is an in-game stop watch for Vice City made by MeanpantheR.

Keys: F5 = Start Timer

F6 = Stop Timer (Also shows you your time)

F7 = Reset Time

F8 = Show your Time

The orginal forum thread can be found [here](http://forum.mtasa.com/viewtopic.php?t=12565).

MTASG
-----

This is a script from Wartech that can display statistics about a server on a web page.

The original forum thread can be found [here](http://forum.mtasa.com/viewtopic.php?t=4341).

MTA-AntiCheat
-------------

A client/server program that monitors a user's files for known cheats and hacks. If any are found, the MTA-AC program running on the server is informed and the player is kicked. This was never completed, as eAi was shortly afterwards recruited to the MTA team.

The orginal forum thread can be found [here](http://forum.mtasa.com/viewtopic.php?t=5908).

MTA Sever Stat Fetcher
----------------------

A server statistics program by 404 for use on web servers.

The orginal forum thread can be found [here](http://forum.mtasa.com/viewtopic.php?t=10361).

phpMTAS
-------

Another web-based statistics script. This time by dusty

The orginal forum thread can be found [here](http://forum.mtasa.com/viewtopic.php?t=5244).

PHP server query tool
---------------------

Andy\_1984 published on July 6th 2005 an mIRC script which allow you to query MTA-servers with use of the All Seeing Eye-server.

The orginal forum thread can be found [here](http://forum.mtasa.com/viewtopic.php?t=13121).
