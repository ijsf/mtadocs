<pageclass class="#AA7592" subcaption="Sockets Module"></pageclass>

This function writes data to a socket.

Syntax
------

``` lua
bool sockWrite ( socket theSocket, string data)
```

### Required arguments

-   **theSocket:** The socket to write the data to.
-   **data:** The data you wanna send.

### Returns

Returns *a boolean* true if the data was send, false otherwise.

Example
-------

This piece of code connects to irc.gtanet.com, joins \#mta and quits in 10 seconds.

``` lua
local root = getRootElement()
local ircSocket = sockOpen("irc.gtanet.com",6667)

addEventHandler("onSockOpened",root,
   function (socket)
      if socket == ircSocket then
         sockWrite(socket,"USER mta mta * :Bot\r\n")
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
