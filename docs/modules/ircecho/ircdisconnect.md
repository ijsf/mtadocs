Disconnects an open IRC Connection

Syntax
------

``` lua
function ircDisconnect ( IRCConnection irc )
```

### Required arguments

-   **irc:** The IRCConnection you wish to disconnect

Example
-------

**Example 1:** This example connects to a server on *ResourceStart* and disconnects on *ResourceStop*

``` lua
szChans = {} --Init an array of channels for storage

function onResourceStart( res )
    if res == getThisResource() then -- If the starting resource is this one
        ircInit( ) -- Initialize the module for this resource
        pIRC = ircOpen( "irc.gtanet.com", 6667, "WikiTest", "#channel" ) -- Open the IRC connection
        if pIRC then -- If opening connection was successful
            szChans[ pIRC ] = "#channel" -- Add the channel to the table
        end
    end
end

function onResourceStop( res )
    if res == getThisResource () then -- If the stopping resource is this one
        if pIRC then -- If theres an IRC Connection
            ircDisconnect( pIRC ) -- Disconnect the connection
            szChans[ pIRC ] = nil -- Removes the channel from the array
            pIRC = nil -- Set the connection to nil
        end
    end
end

addEventHandler( "onResourceStart", getRootElement(), onResourceStart )
addEventHandler( "onResourceStop", getRootElement(), onResourceStop )
```

See also
--------
