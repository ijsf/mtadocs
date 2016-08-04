This function returns the current password required to join the server.

Syntax
------

``` lua
string getServerPassword ()
```

### Returns

Returns the current server password as a string if it has a password, if not it returns *nil*.

Example
-------

This example prints the serverpassword to the player

``` lua
function viewPassword ( thePlayer, command )
  -- Put the password in a var
  local password = getServerPassword ()

  -- Check if the server has a password
  -- If the server has an password, echo it
  if password then
    outputChatBox ( "The server password is " .. password, thePlayer )
  
  -- Else print that there isnt any password
  else
    outputChatBox ( "The server doesn't have any password set", thePlayer )
  end
end

-- Add console command 'viewpassword'
addCommandHandler ( "viewpassword", viewPassword )
```

See Also
--------
