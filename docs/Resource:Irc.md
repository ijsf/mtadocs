The “irc” resource provides an echobot that outputs information such as chatmessages on a irc channel. Information about “irc” or “Internet Relay Chat” can be found on [Wikipedia.](http://en.wikipedia.org/wiki/Irc)

Installation
------------

To get this resource working on your Linux or Windows server, follow these steps:

-   **Install the sockets module**
    -   **Download the module**: You can download the module on the [mta-modules project](http://code.google.com/p/multitheftauto-modules/downloads/list). Download the ml\_sockets.dll file for Windows and the ml\_sockets.so file for Linux
    -   **Put the module in the MTA folder**: In order for MTA to load the module it must be placed in the mods/deathmatch/modules folder, if this folder does not exist yet, make it.
    -   **Add the module to the mtaserver.conf file**: To load the module when the MTA server starts, put this line <module src="ml_sockets.dll"/> in your config file for Windows and <module src="ml_sockets.so"/> in the config file for Linux.
-   **Install the IRC resource**
    -   **Download the resource**: The IRC resource can be found on the [community](http://community.mtasa.com/index.php?p=resources&s=details&id=731), put it in the resources folder.
    -   **Mod the settings.xml file**: Open this file and follow the instructions inside to configure the IRC bot.
    -   **Mod the meta.xml file**: In this file a few settings can be found regarding ads and ingame gui's, **do not mod anything else!** You can also change these settings in the admin panel once the resource has been loaded.
    -   **Acl rights** The resource needs a couple of acl rights in order to work properly, including addBan, kickPlayer & callRemote. Any missing rights will prevent the resource from loading and will output a message in the console.

Now you can run the resource, if the server was running during this installation proces you will have to do /loadmodule ml\_sockets.dll or /loadmodule ml\_sockets.so and /refreshall before doing /start irc

The acl.xml file
----------------

The acl.xml file inside the irc resource takes care of the acl rights for irc commands.

Syntax

``` xml
<command name="!kick" level="2" echoChannelOnly="true" />
```

-   The name is the command including the exclamation mark
-   The level is the minimum level the irc user needs to have in order to use this command
-   The echoChannelOnly is wether the command can be used outside the echo channel

Elements
--------

All users, channels & servers known by the irc resource are represented by elements.

-   Servers are the following elements type: 'irc-server'
-   Channels are the following elements type: 'irc-channel'
-   Users are the following elements type: 'irc-user'

Level system
------------

The irc resource doesn't use the irc modes system for its acl, instead the modes were replaced with numbers.

-   Owner (~) is now level 5
-   Super Operator (&) is now level 4
-   Operator (@) is now level 3
-   Helper (%) is now level 2
-   Voice (+) is now level 1

All other users without a special mode are level 0

Events
------

During the irc proces some events are triggered to help you write extensions for the irc resource. You may want to use addEvent(“eventName”) to use them.

|          |            |                |
|----------|------------|----------------|
| **Name** | **Source** | **Parameters** |

|                     |                     |     |
|---------------------|---------------------|-----|
| **onIRCConnecting** | server theIRCServer |     |

|                  |                     |     |
|------------------|---------------------|-----|
| **onIRCConnect** | server theIRCServer |     |

|                      |                     |               |
|----------------------|---------------------|---------------|
| **onIRCFailConnect** | server theIRCServer | ``` lua       
                                              string reason  
                                              ```            |

|                   |                 |                                     |
|-------------------|-----------------|-------------------------------------|
| **onIRCUserJoin** | user theIRCUser | ``` lua                             
                                       channel theIRCChannel, string vhost  
                                       ```                                  |

|                         |                 |                                |
|-------------------------|-----------------|--------------------------------|
| **onIRCUserNickChange** | user theIRCUser | ``` lua                        
                                             string oldNick, string newNick  
                                             ```                             |

|                   |                 |                                         |
|-------------------|-----------------|-----------------------------------------|
| **onIRCUserPart** | user theIRCUser | ``` lua                                 
                                       channel theIRCChannel, string theReason  
                                       ```                                      |

**NOTE:** 'theReason' can be nil if 'theUser' has quit without a reason.

|                   |                 |                                                         |
|-------------------|-----------------|---------------------------------------------------------|
| **onIRCUserKick** | user theIRCUser | ``` lua                                                 
                                       channel theIRCChannel, string theReason, user theKicker  
                                       ```                                                      |

**NOTE:** 'theKicker' can be false if 'theUser' was kicked by a service like the NickServ.

|                         |                 |                   |
|-------------------------|-----------------|-------------------|
| **onIRCPrivateMessage** | user theIRCUser | ``` lua           
                                             string theMessage  
                                             ```                |

|                  |                 |                                          |
|------------------|-----------------|------------------------------------------|
| **onIRCMessage** | user theIRCUser | ``` lua                                  
                                      channel theIRCChannel, string theMessage  
                                      ```                                       |

|                        |                 |                   |
|------------------------|-----------------|-------------------|
| **onIRCPrivateNotice** | user theIRCUser | ``` lua           
                                            string theMessage  
                                            ```                |

|                 |                 |                                          |
|-----------------|-----------------|------------------------------------------|
| **onIRCNotice** | user theIRCUser | ``` lua                                  
                                     channel theIRCChannel, string theMessage  
                                     ```                                       |

|                   |                 |                                                                         |
|-------------------|-----------------|-------------------------------------------------------------------------|
| **onIRCUserMode** | user theIRCUser | ``` lua                                                                 
                                       channel theIRCChannel, boolean positive, string theMode, user theSetter  
                                       ```                                                                      |

**NOTE:** 'theSetter' can be false if 'theUser' was opped by a service like the NickServ.

|                      |                       |                                                  |
|----------------------|-----------------------|--------------------------------------------------|
| **onIRCChannelMode** | channel theIRCChannel | ``` lua                                          
                                                boolean positive, string theMode, user theSetter  
                                                ```                                               |

**NOTE:** 'theSetter' can be false if the mode was set by a service like the NickServ.

|                      |                 |                                                         |
|----------------------|-----------------|---------------------------------------------------------|
| **onIRCLevelChange** | user theIRCUser | ``` lua                                                 
                                          channel theIRCChannel, number oldlevel, number newlevel  
                                          ```                                                      |

|                   |                 |                  |
|-------------------|-----------------|------------------|
| **onIRCUserQuit** | user theIRCUser | ``` lua          
                                       string theReason  
                                       ```               |

Exported functions
------------------

These functions can be called from another resource to help you write extensions for the irc resource. Use the exports table or [call](/call.md "wikilink") to use them

Example 1:

``` Lua
    exports.irc:ircConnect("irc.gtanet.com","bot",6667)
```

Example 2:

``` Lua
    call(getResourceFromName("irc"),"ircConnect","irc.gtanet.com","bot",6667)
```

|         |                   |                |
|---------|-------------------|----------------|
| ``` lua 
 returns  
 ```      | **function name** | **Parameters** |
||

|         |                          |                                         |
|---------|--------------------------|-----------------------------------------|
| ``` lua 
 boolean  
 ```      | width='200pt'|**ircHop** | ``` lua                                 
                                      server theIRCServer, (string theReason)  
                                      ```                                      |
||

|         |                          |                                                          |
|---------|--------------------------|----------------------------------------------------------|
| ``` lua 
 boolean  
 ```      | width='200pt'|**ircSay** | ``` lua                                                  
                                      channel theIRCChannel/user theIRCUser, string theMessage  
                                      ```                                                       |
||

|         |                          |                                    |
|---------|--------------------------|------------------------------------|
| ``` lua 
 boolean  
 ```      | width='200pt'|**ircRaw** | ``` lua                            
                                      server theIRCServer, string theRaw  
                                      ```                                 |
||

|         |                           |                                           |
|---------|---------------------------|-------------------------------------------|
| ``` lua 
 boolean  
 ```      | width='200pt'|**ircPart** | ``` lua                                   
                                       channel theIRCChannel, (string theReason)  
                                       ```                                        |
||

|             |                           |                                                                         |
|-------------|---------------------------|-------------------------------------------------------------------------|
| ``` lua     
 irc-channel  
 ```          | width='200pt'|**ircJoin** | ``` lua                                                                 
                                           server theIRCServer, string theChannelName, (string theChannelPassword)  
                                           ```                                                                      |
||

|         |                             |                                                          |
|---------|-----------------------------|----------------------------------------------------------|
| ``` lua 
 boolean  
 ```      | width='200pt'|**ircAction** | ``` lua                                                  
                                         channel theIRCChannel/user theIRCUser, string theMessage  
                                         ```                                                       |
||

|         |                             |                                                              |
|---------|-----------------------------|--------------------------------------------------------------|
| ``` lua 
 boolean  
 ```      | width='200pt'|**ircNotice** | ``` lua                                                      
                                         channel theIRCChannel/user theUserChannel, string theMessage  
                                         ```                                                           |
||

|         |                             |                   |
|---------|-----------------------------|-------------------|
| ``` lua 
 boolean  
 ```      | width='200pt'|**outputIRC** | ``` lua           
                                         string theMessage  
                                         ```                |
||

|         |                              |                                                                                                       |
|---------|------------------------------|-------------------------------------------------------------------------------------------------------|
| ``` lua 
 boolean  
 ```      | width='200pt'|**ircConnect** | ``` lua                                                                                               
                                          string serverHost/IP, string nickname, (number serverPort), (string serverPassword), (boolean secure)  
                                          ```                                                                                                    |
||

**NOTE:** Secure connections are not available yet due to the module not suporting SSL yet.

|         |                               |                                         |
|---------|-------------------------------|-----------------------------------------|
| ``` lua 
 boolean  
 ```      | width='200pt'|**ircIdentify** | ``` lua                                 
                                           server theIRCServer, string thePassword  
                                           ```                                      |
||

|         |                                |                     |
|---------|--------------------------------|---------------------|
| ``` lua 
 boolean  
 ```      | width='200pt'|**ircReconnect** | ``` lua             
                                            server theIRCServer  
                                            ```                  |
||

|         |                                 |                                       |
|---------|---------------------------------|---------------------------------------|
| ``` lua 
 boolean  
 ```      | width='200pt'|**ircDisconnect** | ``` lua                               
                                             server theIRCServer, string theReason  
                                             ```                                    |
||

|         |                                 |                                     |
|---------|---------------------------------|-------------------------------------|
| ``` lua 
 boolean  
 ```      | width='200pt'|**ircChangeNick** | ``` lua                             
                                             server theIRCServer, string newNick  
                                             ```                                  |
||

|         |                                 |         |
|---------|---------------------------------|---------|
| ``` lua 
 table    
 ```      | width='200pt'|**ircGetServers** | ``` lua 
                                             ```      |
||

|         |                                    |                     |
|---------|------------------------------------|---------------------|
| ``` lua 
 string   
 ```      | width='200pt'|**ircGetServerName** | ``` lua             
                                                server theIRCServer  
                                                ```                  |
||

|         |                                    |                     |
|---------|------------------------------------|---------------------|
| ``` lua 
 string   
 ```      | width='200pt'|**ircGetServerHost** | ``` lua             
                                                server theIRCServer  
                                                ```                  |
||

|         |                                    |                     |
|---------|------------------------------------|---------------------|
| ``` lua 
 number   
 ```      | width='200pt'|**ircGetServerPort** | ``` lua             
                                                server theIRCServer  
                                                ```                  |
||

|         |                                    |                     |
|---------|------------------------------------|---------------------|
| ``` lua 
 string   
 ```      | width='200pt'|**ircGetServerPass** | ``` lua             
                                                server theIRCServer  
                                                ```                  |
||

|         |                                    |                     |
|---------|------------------------------------|---------------------|
| ``` lua 
 string   
 ```      | width='200pt'|**ircGetServerNick** | ``` lua             
                                                server theIRCServer  
                                                ```                  |
||

|         |                                     |                     |
|---------|-------------------------------------|---------------------|
| ``` lua 
 boolean  
 ```      | width='200pt'|**ircIsServerSecure** | ``` lua             
                                                 server theIRCServer  
                                                 ```                  |
||

|         |                                        |                     |
|---------|----------------------------------------|---------------------|
| ``` lua 
 table    
 ```      | width='200pt'|**ircGetServerChannels** | ``` lua             
                                                    server theIRCServer  
                                                    ```                  |
||

|          |                                       |                       |
|----------|---------------------------------------|-----------------------|
| ``` lua  
 userdata  
 ```       | width='200pt'|**ircGetChannelServer** | ``` lua               
                                                    channel theIRCChannel  
                                                    ```                    |
||

|         |                                  |                       |
|---------|----------------------------------|-----------------------|
| ``` lua 
 table    
 ```      | width='200pt'|**ircGetChannels** | ``` lua               
                                              (server theIRCServer)  
                                              ```                    |
||

|         |                                     |                                       |
|---------|-------------------------------------|---------------------------------------|
| ``` lua 
 boolean  
 ```      | width='200pt'|**ircSetChannelMode** | ``` lua                               
                                                 channel theIRCChannel, string theMode  
                                                 ```                                    |
||

|         |                                     |                       |
|---------|-------------------------------------|-----------------------|
| ``` lua 
 string   
 ```      | width='200pt'|**ircGetChannelName** | ``` lua               
                                                 channel theIRCChannel  
                                                 ```                    |
||

|         |                                     |                       |
|---------|-------------------------------------|-----------------------|
| ``` lua 
 string   
 ```      | width='200pt'|**ircGetChannelMode** | ``` lua               
                                                 channel theIRCChannel  
                                                 ```                    |
||

|         |                                      |                       |
|---------|--------------------------------------|-----------------------|
| ``` lua 
 table    
 ```      | width='200pt'|**ircGetChannelUsers** | ``` lua               
                                                  channel theIRCChannel  
                                                  ```                    |
||

|         |                                      |                       |
|---------|--------------------------------------|-----------------------|
| ``` lua 
 string   
 ```      | width='200pt'|**ircGetChannelTopic** | ``` lua               
                                                  channel theIRCChannel  
                                                  ```                    |
||

|          |                                         |                       |
|----------|-----------------------------------------|-----------------------|
| ``` lua  
 userdata  
 ```       | width='200pt'|**ircGetChannelFromName** | ``` lua               
                                                      string theChannelName  
                                                      ```                    |
||

|         |                                    |                       |
|---------|------------------------------------|-----------------------|
| ``` lua 
 bool     
 ```      | width='200pt'|**ircIsEchoChannel** | ``` lua               
                                                channel theIRCChannel  
                                                ```                    |
||

|         |                                  |                                 |
|---------|----------------------------------|---------------------------------|
| ``` lua 
 boolean  
 ```      | width='200pt'|**ircSetUserMode** | ``` lua                         
                                              user theIRCUser, string theMode  
                                              ```                              |
||

|         |                                  |                 |
|---------|----------------------------------|-----------------|
| ``` lua 
 string   
 ```      | width='200pt'|**ircGetUserMode** | ``` lua         
                                              user theIRCUser  
                                              ```              |
||

|         |                                  |                 |
|---------|----------------------------------|-----------------|
| ``` lua 
 string   
 ```      | width='200pt'|**ircGetUserNick** | ``` lua         
                                              user theIRCUser  
                                              ```              |
||

|         |                                   |                 |
|---------|-----------------------------------|-----------------|
| ``` lua 
 number   
 ```      | width='200pt'|**ircGetUserLevel** | ``` lua         
                                               user theIRCUser  
                                               ```              |
||

|         |                               |                       |
|---------|-------------------------------|-----------------------|
| ``` lua 
 table    
 ```      | width='200pt'|**ircGetUsers** | ``` lua               
                                           (server theIRCServer)  
                                           ```                    |
||

|          |                                    |                 |
|----------|------------------------------------|-----------------|
| ``` lua  
 userdata  
 ```       | width='200pt'|**ircGetUserServer** | ``` lua         
                                                 user theIRCUser  
                                                 ```              |
||

|         |                                   |                                        |
|---------|-----------------------------------|----------------------------------------|
| ``` lua 
 number   
 ```      | width='200pt'|**ircGetUserLevel** | ``` lua                                
                                               user theIRCUser, channel theIRCChannel  
                                               ```                                     |
||

|         |                                   |                 |
|---------|-----------------------------------|-----------------|
| ``` lua 
 string   
 ```      | width='200pt'|**ircGetUserVhost** | ``` lua         
                                               user theIRCUser  
                                               ```              |
||

|          |                                      |                    |
|----------|--------------------------------------|--------------------|
| ``` lua  
 userdata  
 ```       | width='200pt'|**ircGetUserFromNick** | ``` lua            
                                                   string theNickname  
                                                   ```                 |
||

|         |                                        |                                                                                                                         |
|---------|----------------------------------------|-------------------------------------------------------------------------------------------------------------------------|
| ``` lua 
 bool     
 ```      | width='200pt'|**addIRCCommandHandler** | ``` lua                                                                                                                 
                                                    string theCommandName, function theFunctionToCall/string functionName, (number minimumLevel), (boolean echoChannelOnly)  
                                                    ```                                                                                                                      |
||

**NOTE:** Use a string with the function name for the second argument if your are calling this function from another resource, also make sure the function is exported.

|         |                                  |         |
|---------|----------------------------------|---------|
| ``` lua 
 table    
 ```      | width='200pt'|**ircGetCommands** | ``` lua 
                                              ```      |
||

|         |                                      |                   |
|---------|--------------------------------------|-------------------|
| ``` lua 
 number   
 ```      | width='200pt'|**ircGetCommandLevel** | ``` lua           
                                                  string theCommand  
                                                  ```                |
||

|         |                                               |                   |
|---------|-----------------------------------------------|-------------------|
| ``` lua 
 boolean  
 ```      | width='200pt'|**ircIsCommandEchoChannelOnly** | ``` lua           
                                                           string theCommand  
                                                           ```                |
||

**NOTE:** All parameters that are between brackets are optional, see [optional arguments](/optional_arguments.md "wikilink")

Commands
--------

|             |                         |
|-------------|-------------------------|
| **command** | width='100pt'|**level** |
||

|           |                     |
|-----------|---------------------|
| **!kick** | width='100pt'|**2** |
||

|             |                     |
|-------------|---------------------|
| **!uptime** | width='100pt'|**0** |
||

|          |                     |
|----------|---------------------|
| **!say** | width='100pt'|**0** |
||

|        |                     |
|--------|---------------------|
| **!s** | width='100pt'|**0** |
||

|        |                     |
|--------|---------------------|
| **!m** | width='100pt'|**0** |
||

|              |                     |
|--------------|---------------------|
| **!players** | width='100pt'|**0** |
||

|         |                     |
|---------|---------------------|
| **!pm** | width='100pt'|**0** |
||

|         |                     |
|---------|---------------------|
| **!ts** | width='100pt'|**0** |
||

|            |                     |
|------------|---------------------|
| **!getip** | width='100pt'|**2** |
||

|                |                     |
|----------------|---------------------|
| **!getserial** | width='100pt'|**2** |
||

|           |                     |
|-----------|---------------------|
| **!mute** | width='100pt'|**2** |
||

|             |                     |
|-------------|---------------------|
| **!unmute** | width='100pt'|**2** |
||

|            |                     |
|------------|---------------------|
| **!mutes** | width='100pt'|**2** |
||

|             |                     |
|-------------|---------------------|
| **!freeze** | width='100pt'|**2** |
||

|               |                     |
|---------------|---------------------|
| **!unfreeze** | width='100pt'|**2** |
||

|           |                     |
|-----------|---------------------|
| **!kill** | width='100pt'|**2** |
||

|           |                     |
|-----------|---------------------|
| **!slap** | width='100pt'|**2** |
||

|          |                     |
|----------|---------------------|
| **!ban** | width='100pt'|**3** |
||

|            |                     |
|------------|---------------------|
| **!banip** | width='100pt'|**3** |
||

|                |                     |
|----------------|---------------------|
| **!banserial** | width='100pt'|**3** |
||

|              |                     |
|--------------|---------------------|
| **!banname** | width='100pt'|**3** |
||

|              |                     |
|--------------|---------------------|
| **!unbanip** | width='100pt'|**3** |
||

|                  |                     |
|------------------|---------------------|
| **!unbanserial** | width='100pt'|**3** |
||

|            |                     |
|------------|---------------------|
| **!unban** | width='100pt'|**3** |
||

|           |                     |
|-----------|---------------------|
| **!bans** | width='100pt'|**3** |
||

|               |                     |
|---------------|---------------------|
| **!commands** | width='100pt'|**0** |
||

|           |                     |
|-----------|---------------------|
| **!cmds** | width='100pt'|**0** |
||

|          |                     |
|----------|---------------------|
| **!lua** | width='100pt'|**4** |
||

|          |                     |
|----------|---------------------|
| **!run** | width='100pt'|**4** |
||

|           |                     |
|-----------|---------------------|
| **!crun** | width='100pt'|**4** |
||

|                |                     |
|----------------|---------------------|
| **!resources** | width='100pt'|**3** |
||

|            |                     |
|------------|---------------------|
| **!start** | width='100pt'|**3** |
||

|              |                     |
|--------------|---------------------|
| **!restart** | width='100pt'|**3** |
||

|           |                     |
|-----------|---------------------|
| **!stop** | width='100pt'|**3** |
||

|              |                     |
|--------------|---------------------|
| **!account** | width='100pt'|**3** |
||

|                |                     |
|----------------|---------------------|
| **!community** | width='100pt'|**3** |
||

|            |                     |
|------------|---------------------|
| **!money** | width='100pt'|**0** |
||

|             |                     |
|-------------|---------------------|
| **!health** | width='100pt'|**0** |
||

|                  |                     |
|------------------|---------------------|
| **!wantedlevel** | width='100pt'|**0** |
||

|           |                     |
|-----------|---------------------|
| **!team** | width='100pt'|**0** |
||

|           |                     |
|-----------|---------------------|
| **!ping** | width='100pt'|**0** |
||

|              |                     |
|--------------|---------------------|
| **!modules** | width='100pt'|**3** |
||

|                |                     |
|----------------|---------------------|
| **!changemap** | width='100pt'|**3** |
||

|          |                     |
|----------|---------------------|
| **!map** | width='100pt'|**0** |
||

|               |                     |
|---------------|---------------------|
| **!shutdown** | width='100pt'|**5** |
||

|               |                     |
|---------------|---------------------|
| **!password** | width='100pt'|**4** |
||

|              |                     |
|--------------|---------------------|
| **!gravity** | width='100pt'|**3** |
||

|              |                     |
|--------------|---------------------|
| **!weather** | width='100pt'|**3** |
||

|             |                     |
|-------------|---------------------|
| **!server** | width='100pt'|**0** |
||

|           |                     |
|-----------|---------------------|
| **!zone** | width='100pt'|**0** |
||

|                 |                     |
|-----------------|---------------------|
| **!refreshall** | width='100pt'|**4** |
||

|              |                     |
|--------------|---------------------|
| **!refresh** | width='100pt'|**4** |
||

|               |                     |
|---------------|---------------------|
| **!checkmap** | width='100pt'|**2** |
||

|              |                     |
|--------------|---------------------|
| **!country** | width='100pt'|**2** |
||

Modding
-------

Please don't mod the resource, you might break it and cause it to malfunction or to spam errors. If this happens you will not get any support. Write extensions instead.

Contact
-------

The author (MCvarial) can be contacted using IRC (\#mta,\#mta.dutch) Or by email (MCvarial@gmail.com)

[nl:<Resource:Irc>](/nl:Resource:Irc.md "wikilink") [ru:<Resource:Irc>](/ru:Resource:Irc.md "wikilink")
