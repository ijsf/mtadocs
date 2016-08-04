This function changes the password required to join the server to the given string.

Syntax
------

``` lua
bool setServerPassword ( string thePassword )
```

### Required Arguments

-   **thePassword:** The new server password you want. Pass *nil* or an empty string to remove the password.

### Returns

Returns *true* if the password was successfully changed or removed, *false* or *nil* otherwise.

Example
-------

This example adds two commands for you to use: setpassword and removepassword.

``` lua
addCommandHandler( "setpassword", -- add a command handler for the command
   function( thePlayer, command, password )
      if #password < 3 then -- check if the password is shorter than 3 letters
         outputChatBox( "The password needs to be atleast 3 letters long!", thePlayer ) -- tell the player that password was too short
         return -- abort command
      end
      local success = setServerPassword( password ) -- check whether changing password worked
      if success then
         outputChatBox( "Server password change to: " .. password, thePlayer ) -- if it did, tell the player
      else
         outputChatBox( "Failed to change servers password.", thePlayer ) -- if it didn't, tell the player
      end
   end
)

addCommandHandler( "removepassword", -- add a command handler for the command
   function( thePlayer, command )
      local success = setServerPassword( nil ) -- check whether removing password worked
      if success then
         outputChatBox( "Server password removed successfully", thePlayer ) -- if it did, tell the player
      else
         outputChatBox( "Failed to remove servers password.", thePlayer ) -- if it didn't, tell the player
      end
   end
)
```

See Also
--------
