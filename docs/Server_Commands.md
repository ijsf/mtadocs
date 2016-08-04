This page lists all built in commands that the server can process. All these commands can be entered via the server console or the client console depending upon permissions unless otherwise stated.

Resource commands
-----------------

#### check

  
<ins>Server console only</ins>

Usage: check \[ *all* | *<resource-name>* \]

Checks which files would be changed with [upgrade](/Server_Commands#upgrade.md "wikilink") command. Does not modify anything.

#### info

  
<ins>Server console only</ins>

Usage: info *<resource-name>*

Get info for a resource eg: info admin

#### list

  
<ins>Server console only</ins>

Shows a list of resources

#### refresh

  
Refresh resource list to find new resources

#### refreshall

  
Refresh resources and restart any changed resources

#### restart

  
Usage: info *<resource-name>*

Restarts a running resource eg: restart admin

#### start

  
Usage: start *<resource-name>*

Start a loaded resource eg: start admin

#### stop

  
Usage: stop *<resource-name>*

Stop a resource eg: stop admin

#### stopall

  
Stop all running resources

#### upgrade

  
<ins>Server console only</ins>

Usage: upgrade \[ *all* | *<resource-name>* \]

Perform a basic upgrade of all resources. The [check](/Server_Commands#checkall.md "wikilink") command shows the list of changes this command will make.

#### aclrequest

  
Usage: aclrequest \[ *list* | *allow* | *deny* \] *<resource-name>* \[ *<right>* | *all* \]

Manage ACL requests from resources implementing <aclrequest> in their [meta.xml](/meta.xml.md "wikilink")

Account commands
----------------

#### aexec

  
Usage: aexec *<nick>* *<command>*

Force a player to execute a command eg: aexec playername say hello

#### addaccount

  
Usage: addaccount *<accountname>* *<password>*

Add an account eg: addaccount accountname password

#### chgpass

  
Usage: chgpass *<accountname>* *<password>*

Change an accounts password eg: chgpass account newpw

#### delaccount

  
Usage: delaccount *<accountname>*

Delete an account eg: delaccount accountname

Server commands
---------------

#### ase

  
<ins>Server console only</ins>

See the amount of master server list queries

#### debugdb

  
Usage: debugdb *&lt;*0-2*&gt;*

<ins>Server console only</ins>

Set logging level for database functions. \[0-Off  1-Errors only  2-All\]

By default, logging output is written to the file **logs/db.log** unless another file is declared in the [<dbfile> section of mtaserver.conf](/Mtaserver.conf#dbfile.md "wikilink")

#### help

  
<ins>Server console only</ins>

Displays these list of commands

#### loadmodule

  
<ins>Server console only</ins>

Usage: loadmodule *<module-filename>*

Load a module eg: loadmodule ml\_sockets.dll

#### unloadmodule

  
<ins>Server console only</ins>

Usage: unloadmodule *<module-filename>*

Unload a module eg: unloadmodule ml\_sockets.dll

#### reloadmodule

  
<ins>Server console only</ins>

Usage: reloadmodule *<module-filename>*

Reload a module eg: reloadmodule ml\_sockets.dll

#### openports

  
<ins>Server console only</ins>

Test if server ports are open

#### shutdown

  
Usage: shutdown *<reason>*

Shutdown the server eg: shutdown put reason here

#### sver

  
Get the server MTA version

Other commands
--------------

#### say

  
Usage: say *<text>*

Show a message to all players on the server eg: say hello

#### whois

  
Usage: whois *<nick>*

Get the IP of a player currently connected (use whowas for IP/serial/version)

#### whowas

  
Usage: whowas *<nick>*

Get IP/Serial/username of a player that was previously connected to the server

#### ver

  
Get the MTA version

Client relevant only
--------------------

#### chgmypass

  
<ins>Client only</ins>

Usage: chgmypass *<oldpass>* *<newpass>*

Change your password eg: chgmypass oldpw newpw

#### debugscript

  
<ins>Client only</ins>

Usage: debugscript *&lt;*0-3*&gt;*

Remove (This does not work “Incorrect client type for this command”)

#### login

  
<ins>Client only</ins>

Usage: login *<accountname>* *<password>*

Login to an account eg: login accountname password

#### logout

  
<ins>Client only</ins>

Log out of the current account

#### me

  
<ins>Client only</ins>

Usage: me *<text>*

Show a message to all players on the server, with your nick prepended

#### msg

  
<ins>Client only</ins>

Usage: msg *<nick>* *<text>*

Send a message to a player eg: msg playername hello

#### nick

  
<ins>Client only</ins>

Usage: nick *<old-nick>* *<new-nick>*

Change your ingame nickname

#### teamsay

  
<ins>Client only</ins>

Usage: teamsay *<test>*

Send a message to all players on the same team

[Category: Support](/Category:_Support.md "wikilink") [ru:Server Commands](/ru:Server_Commands.md "wikilink")
