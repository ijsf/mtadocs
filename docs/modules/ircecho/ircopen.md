Opens a connection to the specified IRC Server

Syntax
------

``` lua
IRCConnection ircOpen ( string hostname, int port, string nick, string channel, [ string password = ""] )
```

### Required arguments

-   **hostname:** The IRC server to connect to
-   **port:** The IRC server port
-   **nick:** The nickname you want your bot to connect as
-   **channel:** The channel you want the bot to join on connect

### Optional arguments

-   **password**: The password to enter the IRC server

### Returns

Returns a pointer to the IRC connection if successful, otherwise it returns *nil*

Example
-------

**Example 1:** This example connects to *irc.gtanet.com* on port *6667* as *WikiTest* and joins *\#Channel*

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

addEventHandler( "onResourceStart", getRootElement(), onResourceStart )
```

See also
--------
