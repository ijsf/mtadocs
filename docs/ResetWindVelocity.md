This function resets the wind velocity in San Andreas to its default state.

Syntax
------

``` lua
bool resetWindVelocity ( )
```

### Returns

Returns true if successful, false otherwise.

Example
-------

<section name="Client" class="client" show="true">
This example returns the wind velocity to a player if they use the command 'resetwindvelocity'.

``` lua
function commandResetWindVelocity()
   resetWindVelocity()
   outputChatBox("Wind velocity reset to default", 0, 255, 0)
end
addCommandHandler("resetwindvelocity", commandResetWindVelocity)
```

</section>
<section name="Server" class="server" show="true">
This example returns the wind velocity for all players if they use the command 'resetwindvelocity'.

``` lua
function commandResetWindVelocity()
   resetWindVelocity()
   outputChatBox("Wind velocity reset to default", root, 0, 255, 0)
end
addCommandHandler("resetwindvelocity", commandResetWindVelocity)
```

</section>
See Also
--------
