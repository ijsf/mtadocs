This function gets the given radio channel name.

Syntax
------

``` lua
string getRadioChannelName ( int id )             
```

### Required Arguments

-   **id:** The ID of the radio station you want to get the name of. It is a number from 0 to 12.

### Returns

Returns a string containing the station name if successful, *false* otherwise.

Example
-------

<section name="Client" class="client" show="true">
``` lua
addCommandHandler("getradio",
    function()
        outputChatBox("You're currently listening to "..getRadioChannelName(getRadioChannel()).."!")
    end
)
```

</section>
See Also
--------

[AR:getRadioChannelName](/AR:getRadioChannelName.md "wikilink") [RU:GetRadioChannelName](/RU:GetRadioChannelName.md "wikilink") [PL:GetRadioChannelName](/PL:GetRadioChannelName.md "wikilink")
