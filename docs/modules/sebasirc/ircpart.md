This function will part the bot from a channel

Syntax
------

``` lua
bool ircPart ( string channel [, string reason = "" ] )
```

### Required arguments

-   **channel:** The channel name to part.

### Optional Arguments

-   **reason:** The part reason.

### Returns

Returns true, otherwise false when giving wrong arguments.

Example
-------

``` lua
local bot = nil

addEventHandler("onResourceStart", getResourceRootElement(),
  function()
    if ircConnect("irc.mtasa.com", 6667, "echoBot") then
      bot = true
      ircJoin("#mta.echo")
    end
  end
)

addCommandHandler("part",
  function(thePlayer, command, channel)
    if channel == nil then return end
    
    if bot and ircIsConnected() then
      ircPart(tostring(channel))
      outputChatBox("-IRC- Parted: "..tostring(channel).."!")
    end
  end
)
```

[pl:Modules/SebasIRC/ircPart](/docs/pl:modules/sebasirc/ircpart.md "wikilink")

See also
--------
