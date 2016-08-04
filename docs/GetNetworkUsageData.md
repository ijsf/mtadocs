This function returns a [table](/table.md "wikilink") containing network usage information about inbound and outbound packets.

Syntax
------

``` lua
table getNetworkUsageData ( )
```

### Returns

Returns a [table](/table.md "wikilink") with two fields: “in” and “out”. Each of these contain a table with two fields: “bits” and “count”. Each of these contain a table with 256 numeric fields ranging from 0 to 255, containing the appropriate network usage data for such packet id.

Example
-------

This example adds command *nd* that shows info about all inbound packets with bits bigger than zero.

``` lua
addCommandHandler("nd",
    function ()
        local networkData = getNetworkUsageData()["in"]
        for i, val in pairs(networkData["count"]) do
            if networkData["bits"][i] > 0 then
                outputChatBox("ID: " .. i .. ": " .. val .. " - " .. networkData["bits"][i] .. "b")
            end
        end
end)
```

See Also
--------
