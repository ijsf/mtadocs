### Current version

Current protocol version is [R1.1](/docs/MTA_R1.1_remote_administration_protocol.md "wikilink").

### Notes

This document outlines the network protocol for the Remote Administration system used in Multi Theft Auto : San Andreas Race Modification R1. This document is intended for people to create their own Remote Administration tools if they wish to.

No details will be given on how creation of these tools can be done, please seak outside assistance if help is required in this area. This document is only meant as a guide.

### Warning

THE ADMINISTRATION SYSTEM IN MTA:SA HAS A SCHEDULED OVERHALL PLANNED FOR FUTURE RELEASES. AS A RESULT THE NETCODE IN THIS DOCUMENT WILL BE CHANGING SIGNIFICANTLY. NOTIFICATION OF THIS WILL BE GIVEN WHEN A VERSION IS RELEASED WITH ANY CHANGES.

Packet List
-----------

This is where the packet ID's are detailed. Descriptions of how the individual packets are made up will be given further down.

NOTE: Every packet sent and recieved has a byte of value 0x6D as the 1st byte. This will be denoted as ADMIN\_PACKET\_HEADER throughout this document.

-   ADMIN\_CONNECT = 0x00
-   ADMIN\_DISCONNECT = 0x01
-   ADMIN\_PING = 0x02
-   ADMIN\_CHAT = 0x03
-   ADMIN\_PLAYER\_JOIN = 0x04
-   ADMIN\_PLAYER\_PART = 0x05
-   ADMIN\_PLAYER\_LOGIN = 0x06
-   ADMIN\_KICK = 0x07
-   ADMIN\_BAN = 0x08
-   ADMIN\_ADDBAN = 0x09
-   ADMIN\_UNBAN = 0x0A
-   ADMIN\_CHANGE\_SERVER\_PASSWORD = 0x0B
-   ADMIN\_SERVER\_SHUTDOWN = 0x0C
-   ADMIN\_PLAYER\_MUTE = 0x0D
-   ADMIN\_PLAYER\_FREEZE = 0x0E
-   ADMIN\_PLAYER\_NICK\_CHANGE = 0x0F
-   ADMIN\_PLAYER\_DEATH = 0x10
-   ADMIN\_PLAYER\_PM = 0x11
-   ADMIN\_RACE\_LIST = 0x12
-   ADMIN\_START\_RACE = 0x13
-   ADMIN\_SET\_MAX\_PLAYERS = 0x14

Packet Description Formating
----------------------------

This is where the packets are described. They will be covered in order of packet ID (Check the enumerations above). Full descriptions of the packets and what is sent and recieved is described.

The packet makeup key is made up of bytes sent (Hexidecimal values are given when there is not an enumeration avaliable).

Strings sent in the bytestream will be denoted like:

`[ string ( description ) ]`

Variable bytes sent will be denoted like:

`[ byte ( description ) ]`

Looped information in packets will be denoted like:

`{ loop < number of times > ( makeup of each itteration of loop ) end-loop }`

ADMIN\_CONNECT
--------------

**Description:**

This is sent to the server to connect to it. The server server will respond depending on whether the attempt was successful or not.

**Packet sent to server:**

`ADMIN_PACKET_HEADER ADMIN_CONNECT 0x01 [ string ( password ) ] 0x7C [ string ( username ) ] 0x00`

**Response packet from server:**

If the connect attempt is successful, the following packet is recieved:

`ADMIN_PACKET_HEADER ADMIN_CONNECT [ byte ( Max players ) ] [ byte ( Current max players ) ] `
`0xFF { loop < Number of players > ( [ byte ( Player ID ) ] [ byte ( Player rcon level ) ] `
`[ byte ( Player mute status ) ] [ byte ( Player frozen status ) ] [ byte ( 1st byte of player IP ) ] `
`[ byte ( 2nd byte of player IP ) ] [ byte ( 3rd byte of player IP ) ] [ byte ( 4th byte of player IP ) ] `
`[ string ( Player Name ) ] 0xFF ) end-loop } 0x00`

If the connect attempt is unsucessful, the following packet is recieved:

`ADMIN_PACKET_HEADER ADMIN_DISCONNECT [ byte ( Disconnect reason ) ]`

**Notes:**

Player rcon level ranges from 0x00 to 0x05 and denotes the level of rcon the player has in the server. Player mute status is either 0x00 (muted) or 0x01 (not muted). Player frozen status is either 0x00 (frozen) or 0x01 (not frozen).

The disconnect reason has the following enumerations:

-   CONNECT\_DISCONNECT = 0x00
-   CONNECT\_FAILED\_BAD\_PASS = 0x01
-   CONNECT\_CONNECTED = 0x02
-   CONNECT\_TIMED\_OUT = 0x03
-   CONNECT\_TOO\_MANY\_USERS\_FROM\_IP = 0x04
-   CONNECT\_BANNED = 0x05
-   CONNECT\_NAME\_IN\_USE = 0x06
-   CONNECT\_INVALID\_VERSION = 0x07

ADMIN\_DISCONNECT
-----------------

**Description:**

This packet is sent when to disconnect from the server. The server will send a response confirming this.

**Packet sent to server:**

`ADMIN_PACKET_HEADER ADMIN_DISCONNECT`

**Response packet from server:**

`ADMIN_PACKET_HEADER ADMIN_DISCONNECT 0x00`

ADMIN\_PING
-----------

**Description:**

This packet is sent from the server to the Remote Admin clients every second. The Remote Admin client should respond.

**Packet recieved from server:**

`ADMIN_PACKET_HEADER ADMIN_PING`

**Packet sent to server in response:**

`ADMIN_PACKET_HEADER ADMIN_PING`

ADMIN\_CHAT
-----------

**Description:**

This is the packet that the server sends for all chat. Remote Admin clients should send this packet to chat.

**Packet sent:**

`ADMIN_PACKET_HEADER ADMIN_CHAT [ string ( Chat text ) ] 0x00`

**Packet sent from server on any chat:**

`ADMIN_PACKET_HEADER ADMIN_CHAT [ byte ( Player ID ) ] [ byte ( Chat type ) ] [ string ( Chat text ) ]`

**Notes:**

`Player ID will be 255 if an Admin or Console are chatting. The chat type has the following enumeration:`

-   ADMIN\_CONSOLE\_CHAT = 0x00
-   ADMIN\_ADMIN\_CHAT = 0x01
-   ADMIN\_PLAYER\_CHAT = 0x02

ADMIN\_PLAYER\_JOIN
-------------------

**Description:**

This packet is recieved from the server when a new player joins the game.

**Packet recieved from server:**

`ADMIN_PACKET_HEADER ADMIN_PLAYER_JOIN [ byte ( Player ID ) ] [ string ( Player name ) ] 0x7C [ byte ( 1st byte of player IP ) ] `
`[ byte ( 2nd byte of player IP ) ] [ byte ( 3rd byte of player IP ) ] [ byte ( 4th byte of player IP ) ]`

ADMIN\_PLAYER\_PART
-------------------

**Description:**

This packet is recieved from the server when a player parts.

**Packet recieved from server:**

`ADMIN_PACKET_HEADER ADMIN_PLAYER_PART [ byte ( Player ID ) ] [ byte ( Part reason ) ]`

**Notes:**

The part reasons have the following enumerations:

-   ADMIN\_PLAYER\_PARTED = 0x00
-   ADMIN\_PLAYER\_KICKED = 0x01
-   ADMIN\_PLAYER\_BANNED = 0x02
-   ADMIN\_PLAYER\_TIMED\_OUT = 0x03

ADMIN\_PLAYER\_LOGIN
--------------------

**Description:**

This packet is recieved from the server when a player logs in to rcon admin.

**Packet recieved from server:**

`ADMIN_PACKET_HEADER ADMIN_PLAYER_LOGIN [ byte ( Player ID ) ] [ byte ( Login type ) ] [ byte ( Rcon level ) ]`

**Notes:**

The rcon level will be between 0x00 and 0x05.

The login type has the following enumerations:

-   ADMIN\_LOGIN\_SUCCESS = 0x00
-   ADMIN\_LOGIN\_FAILED = 0x01
-   ADMIN\_LOGIN\_LOGGED\_IN = 0x02

ADMIN\_KICK
-----------

**Description:**

This packet is sent to the server to kick a player. The response will be a ADMIN\_PLAYER\_PART packet if successful.

**Packet sent:**

`ADMIN_PACKET_HEADER ADMIN_KICK [ byte ( Player ID ) ]`

ADMIN\_BAN
----------

**Description:**

This packet is sent to the server to ban a player. The response will be a ADMIN\_PLAYER\_PART packet if successful.

**Packet sent:**

`ADMIN_PACKET_HEADER ADMIN_BAN [ byte ( Player ID ) ]`

ADMIN\_ADDBAN
-------------

**Description:**

This packet is sent to the server to ban an IP. The server will respond with a packet outlining the outcome.

**Packet sent:**

`ADMIN_PACKET_HEADER ADMIN_ADDBAN [ string ( IP ) ]`

**Response from server:**

`ADMIN_PACKET_HEADER ADMIN_ADDBAN [ byte ( Response ) ]`

**Notes:**

The response has the following enumerations:

-   ADMIN\_BAN\_SUCCESS = 0x00
-   ADMIN\_BAN\_FAILED = 0x01

ADMIN\_UNBAN
------------

**Description:**

This packet is sent to the server to unban an IP. The server will respond with a packet outlining the outcome.

**Packet sent:**

`ADMIN_PACKET_HEADER ADMIN_UNBAN [ string ( IP ) ]`

**Response from server:**

`ADMIN_PACKET_HEADER ADMIN_UNBAN [ byte ( Response ) ]`

**Notes:**

The response has the following enumerations:

-   ADMIN\_UNBAN\_SUCCESS = 0x00
-   ADMIN\_UNBAN\_FAILED = 0x01

ADMIN\_CHANGE\_SERVER\_PASSWORD
-------------------------------

**Description:**

This packet is sent to the server to change the server password, if it is enabled on the server. The server will respond with the outcome.

**Packet sent:**

`ADMIN_PACKET_HEADER ADMIN_CHANGE_SERVER_PASSWORD [ string ( New password ) ]`

**Response from server:**

`ADMIN_PACKET_HEADER ADMIN_CHANGE_SERVER_PASSWORD [ byte ( Response ) ]`

**Notes:**

The response has the following enumerations:

-   ADMIN\_SERVER\_PASSWORD\_CHANGED = 0x00
-   ADMIN\_SERVER\_PASSWORD\_FAILED = 0x01
-   ADMIN\_SERVER\_PASSWORD\_DISABLED = 0x02

ADMIN\_SERVER\_SHUTDOWN
-----------------------

**Description:**

This packet is sent to the server to shut it down, if enabled on the server. The packet must be sent twice within 5 seconds for this to be successful.

**Packet sent:**

`ADMIN_PACKET_HEADER ADMIN_SERVER_SHUTDOWN`

**Response from server:**

`ADMIN_PACKET_HEADER ADMIN_SERVER_SHUTDOWN [ byte ( Response ) ]`

**Notes:**

The response has the following enumerations:

-   ADMIN\_SERVER\_SHUTDOWN\_SUCCESS = 0x00
-   ADMIN\_SERVER\_SHUTDOWN\_WAITING = 0x01
-   ADMIN\_SERVER\_SHUTDOWN\_DISABLED = 0x02

ADMIN\_PLAYER\_MUTE
-------------------

**Description:**

This packet is sent to the server to mute/unmute a player. It is also sent from the server when a player is muted/unmuted and responds to a packet with a success or failure.

**Packet sent:**

`ADMIN_PACKET_HEADER ADMIN_PLAYER_MUTE [ byte ( Player ID ) ] [ byte ( Mute/unmute ) ]`

**Notes:**

The mute/unmute byte has the following enumerations:

-   ADMIN\_PLAYER\_MUTE = 0x00
-   ADMIN\_PLAYER\_UNMUTE = 0x01

**Packet sent from server if successful:**

`ADMIN_PACKET_HEADER ADMIN_PLAYER_MUTE [ byte ( Player ID ) ] [ byte ( Muter ID ) ] [ byte ( Mute/unmute ) ]`

**Notes:**

The muted ID is either a player ID (the player who muted the person) or it is 0xFF for a mute from the Console or 0xFE for a mute from Remote Admin. The Mute/unmute byte has the following enumerations:

-   ADMIN\_MUTE\_SUCCESS = 0x02
-   ADMIN\_UNMUTE\_SUCCESS = 0x03

**Packet sent from the server if unsuccessful:**

`ADMIN_PACKET_HEADER ADMIN_PLAYER_MUTE [ byte ( Player ID ) ] [ byte ( Already muted/unmuted ) ]`

**Notes:**

The already muted/unmuted byte has the following enumerations:

-   ADMIN\_MUTE\_FAILED = 0x00
-   ADMIN\_UNMUTE\_FAILED = 0x01

ADMIN\_PLAYER\_FREEZE
---------------------

**Description:**

This packet is sent to the server to freeze/unfreeze a player. It is also sent from the server when a player is frozen/unfrozen and responds to a packet with a success or failure.

**Packet sent:**

`ADMIN_PACKET_HEADER ADMIN_PLAYER_FREEZE [ byte ( Player ID ) ] [ byte ( Freeze/unfreeze ) ]`

**Notes:**

The freeze/unfreeze byte has the following enumerations:

-   ADMIN\_PLAYER\_FREEZE = 0x00
-   ADMIN\_PLAYER\_UNFREEZE = 0x01

**Packet sent from server if successful:**

`ADMIN_PACKET_HEADER ADMIN_PLAYER_FREEZE [ byte ( Player ID ) ] [ byte ( Freezer ID ) ] [ byte ( Freeze/unfreeze ) ]`

**Notes:**

The Freezer ID is either a player ID (the player who froze the person) or it is 0xFF for a freeze from the Console or 0xFE for a freeze from Remote Admin.

The Freeze/unfreeze byte has the following enumerations:

-   ADMIN\_FREEZE\_SUCCESS = 0x02
-   ADMIN\_UNFREEZE\_SUCCESS = 0x03

**Packet sent from the server if unsuccessful:**

`ADMIN_PACKET_HEADER ADMIN_PLAYER_FREEZE [ byte ( Player ID ) ] [ byte ( Already frozen/unfrozen ) ]`

**Notes:**

The already frozen/unfrozen byte has the following enumerations:

-   ADMIN\_FREEZE\_FAILED = 0x00
-   ADMIN\_UNFREEZE\_FAILED = 0x01

ADMIN\_PLAYER\_NICK\_CHANGE
---------------------------

**Description:**

This packet is sent from the server when a player changes their nickname.

**Packet sent from server:**

`ADMIN_PACKET_HEADER ADMIN_PLAYER_NICK_CHANGE [ byte ( Player ID ) ] [ string ( New nickname ) ]`

ADMIN\_PLAYER\_DEATH
--------------------

**Description:**

This packet is sent from the server when a player dies.

**Packet sent from server:**

`ADMIN_PACKET_HEADER ADMIN_PLAYER_DEATH [ byte ( Player ID ) ]`

ADMIN\_PLAYER\_PM
-----------------

**Description:**

This packet is sent from the server when a player pm's another player.

**Packet sent from server:**

`ADMIN_PACKET_HEADER ADMIN_PLAYER_PM [ byte ( From player ID ) ] [ byte ( To player ID ) ] [ string ( Message ) ]`

ADMIN\_RACE\_LIST
-----------------

**Description:**

This packet is sent with a list of all the races in the server. It is sent on join and when the list changes.

**Packet sent from server:**

`ADMIN_PACKET_HEADER ADMIN_RACE_LIST { loop < number of races > ( [ byte ( Race ID ) ] [ string ( Race name ) ] 0xFF ) end-loop }`

ADMIN\_START\_RACE
------------------

**Description:** This packet is sent to the server to start a race. It is also sent from the server when a new race starts.

**Packet sent:**

`ADMIN_PACKET_HEADER ADMIN_START_RACE [ byte ( Race ID ) ]`

**Packet sent from server:**

`ADMIN_PACKET_HEADER ADMIN_START_RACE [ byte ( Start type ) ] [ byte ( Race ID ) ]`

**Notes:**

Start type has the following enumerations:

-   ADMIN\_RACE\_STARTED = 0x00
-   ADMIN\_RACE\_FAILED = 0x01
-   ADMIN\_RACE\_NO\_PLAYERS = 0x02

ADMIN\_SET\_MAX\_PLAYERS
------------------------

**Description:**

This packet is sent to change the max players of the server. The server will also send a packet when the max players is changed. Note that this number cannot go over the max players in the server config, nor can it ever go above 32.

**Packet sent:**

`ADMIN_PACKET_HEADER ADMIN_SET_MAX_PLAYERS [ byte ( Max players ) ]`

**Response from server:**

`ADMIN_PACKET_HEADER ADMIN_SET_MAX_PLAYERS [ byte ( Max players ) ]`

**Notes:**

Max players will be 0x00 if the attempt to change them failed, otherwise it will be the hexadecimal value of the new number of max players.

[Category:MTA:SA Race](/docs/Category:MTA:SA_Race.md "wikilink")
