Please use [removeBan](/docs/removeBan.md "wikilink")

This function will unban the specified IP.

Syntax
------

``` lua
bool unbanIP ( string ipToUnban, [player unbanningPlayer = nil] )         
```

### Required Arguments

-   **ipToUnban:** The IP that should be unbanned.

### Optional Arguments

-   **unbanningPlayer:** The player who is unbanning the IP. Defaults to nil, meaning no one.

### Returns

Returns *true* if the unban was successful, *false* otherwise.

Example
-------

This example adds a unbanip command for only admins to use (uses a ACL permission check).

``` lua
addCommandHandler( "unbanip", -- add a command handler to command 'unbanip'
   function ( thePlayer, command, ip )
      if ( hasObjectPermissionTo ( thePlayer, "command.unbanip", false ) ) then -- check if the player has access to the command (specified in ACL)
         if not ip then outputChatBox( "No IP specified.", thePlayer ) return end -- if no IP was specified, abort command
         if not findpattern( ip, '[0-9]+\.[0-9]+\.[0-9]+\.[0-9]+', 1 ) then outputChatBox( "Given IP is not valid.", thePlayer ) return end -- if IP is not in correct format, abort command
         local success = unbanIP( ip, thePlayer ) -- see whether the function was a success
         if success then
            outputChatBox( "IP " .. ip .. " succesfully unbanned!", thePlayer ) -- if it was, tell that to player
         else
            outputChatBox( "Unbanning IP " .. ip .. " failed!", thePlayer ) -- if it wasn't, tell that to player
         end
      else
         outputChatBox( "You have no permission to use this command.", thePlayer ) -- tell player that he hasn't got right permission
      end
   end
)

-- specify the findpattern function used in the command handler
function findpattern(text, pattern, start)
    local found = string.find(text, pattern, start)
    if found ~= nil then
        return string.gsub(text, found)
    else return nil end
end
```

See Also
--------
