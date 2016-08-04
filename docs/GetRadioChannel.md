This function retrieves the ID of the currently active radio channel.

Syntax
------

``` lua
int getRadioChannel ( )             
```

### Returns

Returns the ID of the radio channel.

Example
-------

This example prints out the name of your current radio station to the chat box.

``` lua
addCommandHandler ( "getradio",
    function ()
        outputChatBox ( "You're currently listening to " .. getRadioChannelName ( getRadioChannel() ) .. "!" )
    end
)
```

See Also
--------

[AR:getRadioChannel](/docs/AR:getRadioChannel.md "wikilink") [RU:GetRadioChannel](/RU:GetRadioChannel.md "wikilink") [PL:GetRadioChannel](/PL:GetRadioChannel.md "wikilink")
