This outputs a line of text to the server's log. This could be useful for debugging.

Syntax
------

``` lua
bool outputServerLog ( string text )              
```

### Required Arguments

-   **text:** The text to be output to the log.

### Returns

Returns *true* if successful, *false* otherwise.

Example
-------

<section name="Server" class="server" show="true">
**Example 1:** This example outputs client logins to the server log.

``` lua
function logClientLogin ( previous_account, current_account )
    outputServerLog ( "Client " .. getPlayerName ( source ) .. " logged in as " .. getAccountName ( current_account ) )
end
addEventHandler ( "onClientLogin", getRootElement(), logClientLogin )
```

**Example 2:** This example outputs the clients position to the server

``` lua
function outputPosition(source)
    local x,y,z = getElementPosition(source)
    outputServerLog(tostring(x) .. "," .. tostring(y) .. "," .. tostring(z))
end
addCommandHandler("op",outputPosition)
```

</section>
See Also
--------
