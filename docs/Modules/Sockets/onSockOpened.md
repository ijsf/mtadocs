<pageclass class="#AA7592" subcaption="Sockets Module"></pageclass>

This event is triggered when a socket was created.

### Parameters

``` lua
userdata socket
```

-   **socket**: userdata representing a socket.

### Source

The [source](/docs/event_system#Event_source.md "wikilink") of this event is the [root element](/root_element.md "wikilink").

Example
-------

This piece of code connects to irc.gtanet.com, joins \#mta and quits in 10 seconds.

``` lua
local root = getRootElement()
local ircSocket = sockOpen("irc.gtanet.com",6667)

addEventHandler("onSockOpened",root,
   function (socket)
      if socket == ircSocket then
         sockWrite(socket,"USER mta mta * :MCvarial & Gamesnert\r\n")
         sockWrite(socket,"NICK mta\r\n")
         sockWrite(socket,"JOIN #mta\r\n")

         outputServerLog("IRC: Connected!")
         setTimer(disconnect,10000,1)
      end
   end
)

addEventHandler("onSockData",root,
   function (socket,data)
      if socket == ircSocket then
         outputServerLog(data)
      end
   end
)

addEventHandler("onSockClosed",root,
   function (socket)
      if socket == ircSocket then
         outputServerLog("IRC: disconnected!")
      end
   end
)

function disconnect ()
   sockClose(ircSocket)
end
```

See Also
--------

### Functions

### Events
