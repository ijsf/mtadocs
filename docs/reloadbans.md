This function will reload the server ban list file.

Syntax
------

``` lua
bool reloadBans()
```

### Returns

Returns *true* if the ban list was reloaded successfully, *false* otherwise.

Example
-------

This example add command “reloadban” to reload the server ban list file.

``` lua
function ReBan (player)
   if (reloadBans()) then
      outputChatBox("Bans has been reloaded successfully.",player)
   else
      outputChatBox("Failed to Reload Bans.",player)
   end
end
addCommandHandler("reloadban",ReBan)
```

Requirements
------------

See Also
--------
