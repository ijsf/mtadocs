This function returns network status information.

Syntax
------

<section name="Client" class="client" show="true">
``` lua
table getNetworkStats ( )
```

</section>
<section name="Server" class="server" show="true">
``` lua
table getNetworkStats ( [ element thePlayer = nil ] )
```

</section>
### Optional Arguments

-   **thePlayer:** The player you want to retrieve network stats from.

### Returns

Returns a table, the indexes in the table are the following:

-   **bytesReceived** - Total number of bytes received since the connection was started
-   **bytesSent** - Total number of bytes sent since the connection was started
-   **packetsReceived** - Total number of packets received since the connection was started
-   **packetsSent** - Total number of packets sent since the connection was started
-   **packetlossTotal** - (0-100) Total packet loss percentage of sent data, since the connection was started
-   **packetlossLastSecond** - (0-100) Packet loss percentage of sent data, during the previous second
-   **messagesInSendBuffer**
-   **messagesInResendBuffer** - Number of packets queued to be resent (due to packet loss)
-   **isLimitedByCongestionControl**
-   **isLimitedByOutgoingBandwidthLimit**
-   **encryptionStatus**

Example
-------

<section name="Client" class="client" show="true">
This example outputs the local players network status information to their console when using the /netstatus command

``` lua
function netStatus()
    for index, value in pairs(getNetworkStats()) do
        outputConsole(index..": "..value)
    end
    outputChatBox("Network status output to console", 0, 255, 0)
end
addCommandHandler("netstatus", netStatus)
```

This example outputs a warning to local player if packet loss occured in the last second

``` lua
function packetLossCheck()
    local loss = getNetworkStats()["packetlossLastSecond"]
    if (loss > 0) then
        outputChatBox("Packet loss detected when communicating with server, gameplay may be affected", 255, 0, 0)
    end
end
setTimer(packetLossCheck, 1000, 0)
```

This example tracks the average and peak packetloss over the last 60 seconds **PLEASE NOTE:** this example is untested.

``` lua
PACKETLOSS_HISTORY_LENGTH = 60  -- Sample period in seconds
packetlossHistory = {}
packetlossAvg = 0       -- (Output) Average packet loss over last 60 seconds
packetlossPeak = 0      -- (Output) Peak packet loss over last 60 seconds

function samplePacketLoss()
    table.insert( packetlossHistory, getNetworkStats().packetlossLastSecond )
    while( #packetlossHistory > PACKETLOSS_HISTORY_LENGTH ) do
        table.remove( packetlossHistory, 1 )
    end
    packetlossAvg = 0
    packetlossPeak = 0
    for _,value in ipairs(packetlossHistory) do
        packetlossAvg = packetlossAvg + value
        packetlossPeak = math.max( packetlossPeak, value )
    end
    packetlossAvg = packetlossAvg / #packetlossHistory
end

setTimer(samplePacketLoss,1000,0)
```

</section>
See Also
--------
