This function can be used to strip out wanted IRC specific text features (bolding, colouring...).

Syntax
------

``` lua
string ircStrip ( string text, [ string options = "burc" ] )
```

### Required Arguments

-   **text:** The wanted [string](/docs/string.md "wikilink") which is going to be stripped out it's text features.

### Optional Arguments

-   **options:** A string representing the strip options. It is formed from single letters, each having it's own role in the final result.
    -   **b:** Strip out all **bold** text.
    -   **u:** Strip out all <u>underlined</u> text.
    -   **r:** Strip out all <span style="color:white; background:black;">reversed</span> text.
    -   **c:** Strip out all <span style="color:blue; background:orange;">coloured</span> text.

  
By default all text features are removed.

### Returns

Returns the stripped out version of the string if passed arguments were valid, *false* otherwise.

Example
-------

This example creates an ircbot called *DummyBot* makes it connect to a server and join a channel. Once joining the channel, bot will be echoing all IRC channel text to server log, stripping off all IRC specific text features.

``` lua
function resourceStart ( )
    theBot = ircCreateBot ( "DummyBot" )
    ircConnect ( theBot, "irc.gtanet.com", 6667 )
end
addEventHandler ( "onResourceStart", getResourceRootElement ( getThisResource() ), resourceStart )

function event_ircOnConnect ( theBot )
    setTimer ( ircJoinChannel, 2000, 1, theBot, "#testchannel" )
end

function event_ircOnText ( theBot, channel, sender, message )
    outputServerLog ( "[IRC-ECHO] On " .. channel .. "; " .. sender .. ": " .. ircStrip ( message ) )
end
```

See Also
--------
