This function returns the [serial](/docs/serial.md "wikilink") for a specified [player](/player.md "wikilink").

Syntax
------

``` lua
string getPlayerSerial ( player thePlayer )
```

### Required Arguments

-   **thePlayer:** A [player](/docs/player.md "wikilink") object referencing the specified player.

Returns
-------

Returns the serial as a *string* if it was found, *false* otherwise.

Serverside examples
-------------------

This example creates a command with which player can check their own serial.

``` lua
function checkMySerial( thePlayer, command )
    local theSerial = getPlayerSerial( thePlayer )
    if theSerial then
        outputChatBox( "Your serial is: " .. theSerial, thePlayer )
    else
        outputChatBox( "Sorry, you have no serial. =(", thePlayer )
    end
end
addCommandHandler( "myserial", checkMySerial )
```

This example adds a command to ban a player's serial.

``` lua
local function banSerialCommand ( source, command, playerName, reason )
   if playerName then
      local player, serial = getPlayerFromName ( playerName ), getPlayerSerial ( playerName )
      if player then
         addBan ( serial, source, reason )
      end
   end
end
addCommandHandler ( "banplayerserial", banSerialCommand )
```

This example only allows clients with a certain serial to log in into an account.

``` lua
local allowedAccountSerials = 
{
    -- List of allowed serials to log in into an account. Format:
    -- [ Account name ] = { Allowed serial array }
    [ "3ash8" ] = { "9C9F3B55D9D7BB7135FF274D3BF444E4" },
    [ "test5" ] = { "1D6F76CF8D7193792D13789849498452" },
}
 
addEventHandler("onPlayerLogin", root,
    function(_, account)
        -- Get the player serial and the allowed serial list for that account
        -- (If no serial is allowed for the account, do not allow the player to log in as a safety measure)
        local playerSerial, allowedSerials = getPlayerSerial(source), allowedAccountSerials[getAccountName(account)] or ""
        -- Check whether the client has an allowed serial or not
        for i = 1, #allowedSerials do
            if allowedSerials[i] == playerSerial then
                -- The serial is allowed. Proceed with the normal log in proccess
                return
            end
        end
        -- If we reach this point the serial is not allowed. Do not let the player log in
        cancelEvent(true, "Client serial not allowed to log in into the account")
    end
)
```

See Also
--------
