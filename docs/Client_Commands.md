This page lists all built in commands that the client can process. These commands can be entered directly to the client console or via the chatbox by putting a / (forward slash) in front of them. Some [server commands](/Server_Commands.md "wikilink") are also accessible from the client. Arguments inside \[...\] are optional.

Core commands
-------------

#### help

  
Displays these list of commands

#### exit

  
Exits the application

#### quit

  
Exits the application

#### ver

  
Outputs the MTA version in the client console

#### time

  
Outputs the local time in the chatbox

#### showhud

  
Usage: showhud \[*&lt;*0-1*&gt;*\]

Shows the HUD

#### binds

  
Outputs all the binds in the client console

#### serial

  
Outputs your serial in the client console

#### connect

  
Usage: connect *<host> <port>* \[*<nick> <pass>*\]

Connects to a server

#### reconnect

  
Connects to a previous server

#### bind

  
Usage: bind *<defaults/key>* \[*<up/down>*\] *<command>* \[*<arguments>*\]

Binds a key

  
Example to bind X to hiding the HUD: **bind x down showhud 0**

Example to reset all binds: **bind defaults**

#### unbind

  
Usage: unbind *<all/key>* \[*<up/down> <command>*\]

Unbinds a key

  
Example to unbind X to from hiding the HUD: **unbind x down showhud 0**

Example to unbind all commands from X: **unbind x**

#### copygtacontrols

  
Copies the default gta controls - This may require a restart to work properly

#### screenshot

  
Saves a screenshot

#### saveconfig

  
Immediately saves the config

Commands when connected to a server
-----------------------------------

#### sinfo

  
Prints information and settings for the current server into the client console

#### disconnect

  
Disconnect from the server and return to the main menu

#### shownametags

  
Usage: shownametags \[*&lt;*0-1*&gt;*\]

Shows the nametags

#### showchat

  
Usage: showchat \[*&lt;*0-1*&gt;*\]

Shows the chatbox

#### shownetstat

  
Usage: shownetstat \[*&lt;*0-1*&gt;*\]

Shows the network statistics

#### showmemstat

  
Usage: showmemstat \[*&lt;*0-1*&gt;*\]

Shows the memory statistics

#### showframegraph

  
Usage: showframegraph \[*&lt;*0-1*&gt;*\]

Shows the frame rate history graph

#### chatbox

  
Usage: chatbox *&lt;*0-255*&gt;* *&lt;*0-255*&gt;* *&lt;*0-255*&gt;*

Defines the chatbox color

#### textscale

  
Usage: textscale *&lt;*0.8 to 3.0*&gt;*

Defines the scale multiplier of all text-displays

#### showcol

  
Usage: showcol \[*&lt;*0-1*&gt;*\]

Shows colshapes in wireframe for help when writing scripts

Only works in development mode.

More information: [setDevelopmentMode](/setDevelopmentMode.md "wikilink")

#### showsound

  
Usage: showsound \[*&lt;*0-1*&gt;*\]

Prints world sound ids in the debug output windows to help when writing scripts with [setWorldSoundEnabled](/setWorldSoundEnabled.md "wikilink")

Only works in development mode.

More information: [setDevelopmentMode](/setDevelopmentMode.md "wikilink")

Commands for key binds
----------------------

#### cleardebug

  
Clears the debug view

#### chatscrollup

  
Usage: chatscrollup 1

Scrolls the chatbox upwards

#### chatscrolldown

  
Usage: chatscrolldown -1

Scrolls the chatbox downwards

#### debugscrollup

  
Usage: debugscrollup 1

Scrolls the debug view upwards

#### debugscrolldown

  
Usage: debugscrolldown -1

Scrolls the debug view downwards

#### voiceptt

  
Transmits voice to other players

#### enter\_passenger

  
Enters a car as passenger

#### radio\_next

  
Next radio channel

#### radio\_previous

  
Previous radio channel

#### radar

  
Usage: radar \[*&lt;*0-1*&gt;*\]

Shows the radar view

#### radar\_zoom\_in

  
Zooms the radar in

#### radar\_zoom\_out

  
Zooms the radar out

#### radar\_move\_north

  
Moves the radar north

#### radar\_move\_south

  
Moves the radar south

#### radar\_move\_east

  
Moves the radar east

#### radar\_move\_west

  
Moves the radar west

#### radar\_attach

  
Attaches the radar

#### msg\_target

  
Usage: msg\_target *<text>*

Sends a message to the targeted player

#### vehicle\_next\_weapon

  
Changes to the next weapon whilst in a vehicle

#### vehicle\_previous\_weapon

  
Changes to the previous weapon whilst in a vehicle

#### radio\_next

  
Selects the next radio station

#### radio\_previous

  
Selects the previous radio station

[Category: Support](/Category:_Support.md "wikilink") [ru:Client Commands](/ru:Client_Commands.md "wikilink") [hu:Client Commands](/hu:Client_Commands.md "wikilink")
