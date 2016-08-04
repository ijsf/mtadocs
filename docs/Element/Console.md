The Server Console class represents the server console.

The element type of this class is **“console”**.

Commands
--------

In the server console you can use many different commands, affecting the players using the server. Please note that only console commands can be used, and that some commands can not be used through the in-game client console, only through the Server Console.

[<File:Mta_console_help.png>](/File:Mta_console_help.png.md "wikilink")

Note that the console list does not show the usage of the commands. Some commands may also not be listed (possibly related to the [admin](http://wiki.multitheftauto.com/wiki/Admin) resource.(unconfirmed)).

Definitions
===========

**update**:

**stopall**: Stops all the resources.

**refreshall**: Refresh resources and restart any changed resources.

**install**:

**say**: Usage: say <text> | Shows a message to all players on the server eg:“say hello” .

**me**:

**logout**: This would log the console out of its account. (***Please NOTE*** that, if you log the console out, you can't get back in, unless you shutdown and start the server again.)

**delaccount**: Usage: delaccount <accountname>| Delete an account eg:“delaccount Console” &lt;***NOT RECOMMENDED***.

**aexec**: Usage: aexec <nick> <command>| Force a player to execute a command eg: aexec playername say hello.

**debugscript**: Usage: debugscript &lt;0-3&gt;. (***Please NOTE*** that, this is only for client's.)

**ver**: Outputs the server version.

**openports**: Outputs whether the ports “serverport”,“httpport”,“aseport” is open or closed.(if they are closed, please see this topic on how to open it: <http://forum.mtasa.com/viewtopic.php?f=114&t=33722&p=444572#p352164> )

**aclrequest**: Usage: aclrequest \[list|allow|deny\] <resource-name> \[<right>|all\]| Manage ACL requests from resources implementing <aclrequest> in their [meta.xml](/meta.xml.md "wikilink").

**start**: Usage: start <resource-name> | Start a loaded resource eg:“start admin”.

**restart**: Usage: info <resource-name> | Restarts a running resource eg:“restart admin”.

**list**: Shows a list of resources.

**teamsay**: N/A

**nick**: Usage: nick <new-nick> | Please note that only players can change their nick.

**chgmypass**: Usage: chgmypass <oldpass> <newpass> | Please note that you can't change the console password even if you knew the old password.

**chgpass**: Usage: chgpass <nick> <pass> | Changes the players password.

**whois**: Usage: whois <nick> | Outputs the players ip and something else(maybe port).

**help**: Outputs the list of commands shown in the picture above.

**sver**: Outputs the server version.

**debugdb**: Usage: debugdb &lt;0-2&gt; | 0-Disables database debug logging, 1-Only outputs the errors, 2-Outputs all queries.

**stop**: Usage: stop <resource-name> | Stops a running resource.

**refresh**: Checks for newly added resources.

**info**: Usage: info <resource-name> | Outputs the info of the resource. Example: info admin

Outputs:

`Status: Running    Dependents: 0`
`Included resources: 0`
`Files: 190`

**check**: Usage: check \[all|<resource-name>\] | Check resources for deprecated functions and MTA version issues.

**upgrade**: Usage: upgrade \[all|<resource-name>\] | Fixes deprecated functions and MTA version issues in resources.

**msg**: Usage: msg <nick> <message> | Outputs the message to the player.

**login**: Usage: login <username> <password> | Please note that you can't login with the console.(unless you mistakenly logout the console)

**addaccount**: Usage: addaccount <username> <password> | Adds an account to the server.(Mostly used for new server owners)

**shutdown**: Shuts the server down. (You could also use ctrl+c)

**whowas**: Usage: whowas <nick> | Outputs the player history of connects.

**loadmodule**: Usage: loadmodule <module-name-with-extension> | Loads a module.

**ase**: Outputs the Master Server List queries.

**reloadbans**: Reloads all the bans from 'banlist.xml'.

### See Also

[Server\_Commands](/Server_Commands.md "wikilink")

[Category:Element Types](/Category:Element_Types.md "wikilink")
