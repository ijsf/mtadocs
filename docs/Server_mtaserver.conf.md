This page lists the settings that can be set in the settings file. *Setting from the default **mtaserver.conf** settings file is in italics*.

#### servername

  
*<servername>Default MTA Server</servername>*

This parameter specifies the name the server will be visible as in the ingame server browser and on Game-Monitor. It is a required parameter.

#### serverip

  
''<serverip></serverip>

**ONLY USE THIS PARAMETER IF YOU ARE SURE OF WHAT YOU ARE DOING**

It is generally only needed for professional servers and should be left blank otherwise. This parameter specifies the IP to use for servers that have multiple IP addresses. If left blank, it will default to server's standard local IP address.

SERVERIP SHOULD BE LEFT BLANK UNLESS YOU ARE SURE OF WHAT YOU ARE DOING

People who set this and then ask for support will be the first ones against the wall when the revolution comes

#### serverport

  
''<serverport>22003</serverport>

This parameter specifies the UDP port on which the server will be accepting incoming player connections;

default value: 22003. It is a required parameter.

#### maxplayers

  
''<maxplayers>32</maxplayers>

This parameter specifies the number of maximum player slots available on the server;

default value: 32. It is a required parameter.

#### httpserver

  
''<httpserver>1</httpserver>

This parameter specifies whether the builtin http server will be used.

Values: 0 - disabled , 1 - enabled ; default value: 1. Optional parameter.

More information: [Using the web interface](/docs/Server_Manual#Using_the_web_interface.md "wikilink")

#### httpport

  
''<httpport>22005</httpport>

This parameter specifies the TCP port on which the server will be accepting incoming http connections. It can be set to the same value as <serverport>. It is a required parameter if <httpserver> is set to 1.

More information: [Using the web interface](/docs/Server_Manual#Using_the_web_interface.md "wikilink")

#### httpdownloadurl

  
''<httpdownloadurl></httpdownloadurl>

If set, this parameter specifies the external URL from which clients will be able to download needed resources ingame. Otherwise they will download them directly from the server.

More information: [Configuring an external web server](/docs/Server_Manual#Configuring_an_external_web_server.md "wikilink")

#### httpmaxconnectionsperclient

  
''<httpmaxconnectionsperclient>5</httpmaxconnectionsperclient>

This parameter limits the number of http connections each client can make. Depending on the type of http server that is used, a lower figure may reduce download timeouts. Only relevant when using an external http server.

Available range: 1 to 8.

#### httpdosthreshold

  
''<httpdosthreshold>20</httpdosthreshold>

This parameter limits the number http connections that an IP can initiate over a short period of time.

Available range: 1 to 100. default value: 20

#### allow\_gta3\_img\_mods

  
''<allow_gta3_img_mods>none</allow_gta3_img_mods>

By default, the server will block the use of locally customized gta3.img player skins.

This setting can be used to allow such mods. Not recommended for competitive servers.

Values: none or peds ; default value: none

'''From server version 1.4.1-9.07268

#### client\_file

  
''&lt;!-- &lt;client\_file name="data/carmods.dat" verify="0" /&gt; --&gt;

By default, the server will block the use of customized GTA:SA data files.

To allow specific client files, add one or more of the above lines.

More information: [Anti-cheat guide](/docs/Anti-cheat_guide.md "wikilink")

#### disableac

  
''<disableac></disableac>

Comma seperated list of disabled anti-cheats.

e.g. To disable anti-cheat \#2 and \#3, use: 2,3

More information: [Anti-cheat guide](/docs/Anti-cheat_guide.md "wikilink")

#### enablesd

  
''<enablesd></enablesd>

Comma seperated list of enabled special detections. A special detection is a type of anti-cheat for (usually) harmless game modifications. Competitive servers may wish to enable special detections, but most servers should leave this setting blank.

e.g. To enable special detection \#12 (disallow custom D3D9.DLL) use: 12

More information: [Anti-cheat guide](/docs/Anti-cheat_guide.md "wikilink")

#### networkencryption

  
''<networkencryption>1</networkencryption>

This parameter specifies whether communications between the server and client is encrypted. Encryption can help prevent network data being viewed and modified.

Values: 0 - disabled , 1 - enabled ; default value: 1. Optional parameter.

This parameter can changed and saved while the server is running with [setServerConfigSetting](/docs/setServerConfigSetting.md "wikilink")

#### minclientversion

  
''<minclientversion></minclientversion>

Minimum client version. Clients with a lower version will not be allowed to connect. After disconnection, clients will be given an opportunity to download an update. If left blank, this setting is disabled and there are no restrictions on who can connect. Version numbers are described in [getPlayerVersion](/docs/getPlayerVersion.md "wikilink") and look like this: 1.1.0-9.03100.0

This parameter can changed and saved while the server is running with [setServerConfigSetting](/docs/setServerConfigSetting.md "wikilink")

**Note that this setting only determines if the client should be prompted to update. The actual build number they receive will be the [<http://nightly.mtasa.com/ver> highest available](/docs/http://nightly.mtasa.com/ver_highest_available.md "wikilink").**

#### recommendedclientversion

  
''<recommendedclientversion></recommendedclientversion>

Recommended client version. When connecting, if clients have a lower version, they will be given the option to download an update. If left blank, this setting is disabled.

This parameter can changed and saved while the server is running with [setServerConfigSetting](/docs/setServerConfigSetting.md "wikilink")

**Note that this setting only determines if the client should be prompted to update. The actual build number they receive will be the [<http://nightly.mtasa.com/ver> highest available](/docs/http://nightly.mtasa.com/ver_highest_available.md "wikilink").**

#### ase

  
''<ase>1</ase>

This parameter can be used to make the server report to Game-Monitor master servers, allowing it to be visible in the ingame server browser. An additional UDP port needs to be available for this to work (value from <serverport> + 123 , so on a default <serverport> value 22003 the right port will be 22126 ).

Available values: 0 - disabled , 1 - enabled. Optional parameter, defaults to 0.

#### donotbroadcastlan

  
''<donotbroadcastlan>0</donotbroadcastlan>

This parameter allows you to disable LAN broadcasting.

#### password

  
''<password></password>

If set, players will have to provide a password specified below, before they can connect to the server. If left blank, server doesn't require a password from them.

This parameter can changed and saved while the server is running with [setServerPassword](/docs/setServerPassword.md "wikilink") or [setServerConfigSetting](/setServerConfigSetting.md "wikilink")

#### bandwidth\_reduction

  
''<bandwidth_reduction>medium</bandwidth_reduction>

This parameter reduces the server's bandwidth usage by using various optimizations.

Values: none, medium or maximum ; default value: medium

This parameter can be changed and saved while the server is running with [setServerConfigSetting](/docs/setServerConfigSetting.md "wikilink")

#### player\_sync\_interval

  
''<player_sync_interval>100</player_sync_interval>

This parameter determines the time in milliseconds between player sync packets.

Available range: 50 - 500; default value: 100

This parameter can be changed and saved while the server is running with [setServerConfigSetting](/docs/setServerConfigSetting.md "wikilink")

Suggested values for this and the other sync\_interval settings can be found here: [Sync interval settings](/docs/Sync_interval_settings.md "wikilink")

#### lightweight\_sync\_interval

  
''<lightweight_sync_interval>1500</lightweight_sync_interval>

This parameter determines the time in milliseconds between lightweight (player) sync packets.

Available range: 200 - 40000; default value: 1500

This parameter can be changed and saved while the server is running with [setServerConfigSetting](/docs/setServerConfigSetting.md "wikilink")

Suggested values for this and the other sync\_interval settings can be found here: [Sync interval settings](/docs/Sync_interval_settings.md "wikilink")

#### camera\_sync\_interval

  
''<camera_sync_interval>500</camera_sync_interval>

This parameter determines the time in milliseconds between camera sync packets.

Available range: 200 - 400; default value: 500

This parameter can be changed and saved while the server is running with [setServerConfigSetting](/docs/setServerConfigSetting.md "wikilink")

Suggested values for this and the other sync\_interval settings can be found here: [Sync interval settings](/docs/Sync_interval_settings.md "wikilink")

#### ped\_sync\_interval

  
''<ped_sync_interval>400</ped_sync_interval>

This parameter determines the time in milliseconds between ped sync packets.

Available range: 200 - 4000; default value: 400

This parameter can be changed and saved while the server is running with [setServerConfigSetting](/docs/setServerConfigSetting.md "wikilink")

Suggested values for this and the other sync\_interval settings can be found here: [Sync interval settings](/docs/Sync_interval_settings.md "wikilink")

#### unoccupied\_vehicle\_sync\_interval

  
''<unoccupied_vehicle_sync_interval>1000</unoccupied_vehicle_sync_interval>

This parameter determines the time in milliseconds between unoccupied vehicle sync packets.

Available range: 200 - 4000; default value: 1000

This parameter can be changed and saved while the server is running with [setServerConfigSetting](/docs/setServerConfigSetting.md "wikilink")

Suggested values for this and the other sync\_interval settings can be found here: [Sync interval settings](/docs/Sync_interval_settings.md "wikilink")

#### keysync\_mouse\_sync\_interval

  
''<keysync_mouse_sync_interval>100</keysync_mouse_sync_interval>

This parameter determines the minimum time in milliseconds between key sync packets due to mouse movement.

Available range: 50 - 500; default value: 100

This parameter can be changed and saved while the server is running with [setServerConfigSetting](/docs/setServerConfigSetting.md "wikilink")

Suggested values for this and the other sync\_interval settings can be found here: [Sync interval settings](/docs/Sync_interval_settings.md "wikilink")

#### keysync\_analog\_sync\_interval

  
''<keysync_analog_sync_interval>100</keysync_analog_sync_interval>

This parameter determines the minimum time in milliseconds between key sync packets due to joystick movement.

Available range: 50 - 500; default value: 100

This parameter can be changed and saved while the server is running with [setServerConfigSetting](/docs/setServerConfigSetting.md "wikilink")

Suggested values for this and the other sync\_interval settings can be found here: [Sync interval settings](/docs/Sync_interval_settings.md "wikilink")

#### bullet\_sync

  
''<bullet_sync>0</bullet_sync>

This parameter can improve the reliability of shots when using certain weapons. However, it uses more bandwidth.

**It only works on server build 4247 or later, and when enabled, connecting clients will be auto-updated if required.**

Note that bullet sync will be active regardless of this setting when certain [glitches](/docs/setGlitchEnabled.md "wikilink") are enabled.

Values: 0 - disabled , 1 - enabled ; default value: 0.

This parameter can be changed and saved while the server is running with [setServerConfigSetting](/docs/setServerConfigSetting.md "wikilink")

#### vehext\_percent

  
''<vehext_percent>0</vehext_percent>

This parameter sets the amount of extrapolation that clients will apply to remote vehicles.

This can reduce some of the latency induced location disparency by predicting where the remote vehicles will probably be.

Depending on the gamemode, an incorrect prediction may have a negative effect.

Therefore this setting should be considered expermental.

**It only works on server build 4456 or later.**

Available range: 0 to 100. Default - 0 --&gt;

#### vehext\_ping\_limit

  
''<vehext_ping_limit>150</vehext_ping_limit>

This parameter places a limit on how much time (in milliseconds) the vehicle extrapolation will attempt to compensate for.

Only relevant if <vehext_percent> is greater than zero.

**It only works on server build 4456 or later.**

Available range: 50 to 500. Default - 150

#### latency\_reduction

  
''<latency_reduction>0</latency_reduction>

This parameter can reduce the delay of player actions appearing on remote clients by 2 frames (approx 50ms).

Due to the impact this may have on shot lag compensation, it should be considered experimental.

Values: 0 - disabled , 1 - enabled ; default value: 0.

Bugs caused by enabling latency\_reduction: <http://bugs.mtasa.com/view.php?id=8191> + <http://bugs.mtasa.com/view.php?id=8226>

#### threadnet

  
''<threadnet>1</threadnet>

This parameter specifies whether or not to run the network synchronization on another thread.

Enabling will make the sync smoother, but may increase cpu usage slightly.

Values: 0 - disabled , 1 - enabled ; default value: 1.

This parameter can be changed and saved while the server is running with [setServerConfigSetting](/docs/setServerConfigSetting.md "wikilink")

#### idfile

  
''<idfile>server-id.keys</idfile>

Specifies the location and file name of this servers unique private key. This is used to prevent private files saved on the client from being read by other servers.

Keep a backup of this file in a safe place. Default value: server-id.keys

More information about client private files: [Filepath](/docs/Filepath.md "wikilink")

#### logfile

  
''<logfile>logs/server.log</logfile>

Specifies the location and name of the main server log file. If left blank, server won't be saving this file.

#### authfile

  
''<authfile>logs/server\_auth.log</authfile>

As well as the main log file, login successes and failures are logged here for easy reviewing of security issues. If left blank, this file is not used

#### dbfile

  
''<dbfile>logs/db.log</dbfile>

Specifies the location and name of the file used to log database queries. The server command [debugdb](/docs/Server_Commands#debugdb.md "wikilink") sets the amount of logging.

#### acl

  
''<acl>acl.xml</acl>

This parameter specifies the location and name of the Access Control List settings file. If left

blank, server will use acl.xml file, located in the same folder as this configuration file.

#### scriptdebuglogfile

  
''<scriptdebuglogfile>logs/scripts.log</scriptdebuglogfile>

Specifies the location and name of the debugscript log file. If left blank, server won't be saving this file.

#### scriptdebugloglevel

  
''<scriptdebugloglevel>0</scriptdebugloglevel>

Specifies the level of the debugscript log file. Available values: 0, 1, 2, 3. When not set, defaults to 0.

#### fpslimit

  
''<fpslimit>36</fpslimit>

Specifies the frame rate limit that will be applied to connecting clients.

Available range: 25 to 100. Default: 36.

This parameter can be changed and saved while the server is running with [setServerConfigSetting](/docs/setServerConfigSetting.md "wikilink")

#### autologin

  
''<autologin>0</autologin>

Specifies whether or not players should automatically be logged in based on their IP adresses

#### voice

  
''<voice>0</voice>

This parameter specifies whether or not to enable player voice chat in-game

Values: 0 - disabled , 1 - enabled

#### voice\_samplerate

  
''<voice_samplerate>1</voice_samplerate>

This parameter specifies the sample rate for voice chat. 'voice' parameter must be set to 1 for this to be effective. Higher settings use more bandwidth and increase the sampling quality of voice chat

Values: 0 - Narrowband (8kHz), 1 - Wideband (16kHz), 2 - Ultrawideband (32kHz). Default - 1

#### voice\_quality

  
''<voice_quality>4</voice_quality>

This parameter specifies the voice quality for voice chat. 'voice' parameter must be set to 1 for this to be effective. Higher settings use more bandwidth and increase the the overall quality of voice chat

Available range: 0 to 10. Default - 4

#### voice\_bitrate

  
''&lt;!-- &lt;voice\_bitrate&gt;24600&lt;/voice\_bitrate&gt; --&gt;

Specifies the voice bitrate, in bps. This optional parameter overrides the previous two settings. If not set, MTA handles this automatically. Use with care.

#### backup\_path

  
''<backup_path>backups</backup_path>

This parameter specifies the path to use for a basic backup of some server files. Note that basic backups are only made during server startup. Default value: backups

#### backup\_interval

  
''<backup_interval>3</backup_interval>

This parameter specifies the number of days between each basic backup. Backups are only made during server startup, so the actual interval maybe much longer. Setting backup\_interval to 0 will disable backups

Available range: 0 to 30. Default - 3

#### backup\_copies

  
''<backup_copies>5</backup_copies>

This parameter specifies the maximum number of backup copies to keep. Setting backup\_copies to 0 will disable backups

Available range: 0 to 100. Default - 5

#### module

  
''&lt;!-- &lt;module src="sample\_win32.dll"/&gt; --&gt;

''&lt;!-- &lt;module src="sample\_linux.so"/&gt; --&gt;

Specifies the module(s) which are loaded with the server. To load several modules, add more <module> parameter(s). Optional parameter.

#### resource

  
''<resource src="admin" startup="1" protected="0"/>

''<resource src="defaultstats" startup="1" protected="0"/>

''<resource src="helpmanager" startup="1" protected="0"/>

''<resource src="joinquit" startup="1" protected="0"/>

''<resource src="mapcycler" startup="1" protected="0"/>

''<resource src="mapmanager" startup="1" protected="0"/>

''<resource src="parachute" startup="1" protected="0"/>

''<resource src="resourcebrowser" startup="1" protected="1" default="true"/>

''<resource src="resourcemanager" startup="1" protected="1"/>

''<resource src="scoreboard" startup="1" protected="0"/>

''<resource src="spawnmanager" startup="1" protected="0"/>

''<resource src="voice" startup="1" protected="0" />

''<resource src="votemanager" startup="1" protected="0"/>

''<resource src="webadmin" startup="1" protected="0"/>

Specifies persistent resources which are loaded when the server starts. Persistent resources are not stopped even if all the other resources that depend on them stop; that is, the only way to stop them is by explicitly using the *stop* server command or [stopResource](/docs/stopResource.md "wikilink") scripting function. To load several resources, add more <resource> parameters.

<!-- -->

  
In addition, there are several flags which control how the server deals with each resource:

:\* **src**: the resource name. This is the only mandatory flag.

:\* **startup**: controls whether the resource will be started with the server or not. If “1”, “true” or “yes”, the resource will be started. If not specified, defaults to not starting the resource.

:\* **protected**: if “1”, “true” or “yes”, the resource will not be able to be stopped when started. Otherwise, even if not specified, it will default to the normal behaviour.

:\* **default**: if given a “1”, “true” or “yes” value, this resource will be the one who populates the built-in HTTP server main page, which is seen when no resource is given in the web address. It is not possible to have more than one default resource.

[Category: Support](/docs/Category:_Support.md "wikilink") [ru:Server mtaserver.conf](/ru:Server_mtaserver.conf.md "wikilink")
