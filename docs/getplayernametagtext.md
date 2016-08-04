This will allow you to retrieve the name tag a player is currently using.

Syntax
------

``` lua
string getPlayerNametagText ( player thePlayer )
```

### Required Arguments

-   **thePlayer:** The person whose name tag you want to retrieve

### Returns

Returns a *string* with the nametag text, *false* if the player is invalid.

Example
-------

This will output the nametag text of the player who enters the command 'myNametag'.

``` lua
function showNametag ( thePlayer, command )
    local nameTag = getPlayerNametagText ( thePlayer )
    outputChatBox ( "Your nametag text is: " .. nameTag, thePlayer )
end
addCommandHandler("myNametag", showNametag)
```

See Also
--------
