This function will check if the irc bot is connected.

Syntax
------

``` lua
bool ircIsConnected()
```

### Returns

True if connected, otherwise false.

Example
-------

``` lua
addCommandHandler("connected",
  function()
    if ircIsConnected() then
      outputChatBox("-IRC- Connection is ok!")
    else
      outputChatBox("-IRC- Not connected!")
    end
  end
)
```

[pl:Modules/SebasIRC/ircIsConnected](/docs/pl:Modules/SebasIRC/ircIsConnected.md "wikilink")

See also
--------
