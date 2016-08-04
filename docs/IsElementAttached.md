This functions checks whether or not an element is attached to another element.

Syntax
------

``` lua
bool isElementAttached ( element theElement )
```

### Required Arguments

-   **theElement:** The element to check for attachment.

### Returns

Returns *true* if the specified element is attached to another element, *false* if it is not attached or if an improper argument is passed.

Example
-------

This examples checks if a player is attached to anything when they enter a console command:

``` lua
-- add a command handler for 'amiattached' to call the function 'consoleIsPlayerAttached':
function consoleIsPlayerAttached ( thePlayer, command )
   if ( thePlayer ) then -- if a player triggered this command
      local status = isElementAttached ( thePlayer ) -- call the function and store it's result in the 'status' variable
      if ( status ) then -- if the function returned true, tell the player he is attached to something
         outputConsole ( "You are attached to an element!", thePlayer )
      else -- if the function returned false, tell the player he is not attached to anything
         outputConsole ( "You are not attached to an element.", thePlayer )
      end
   end
end
addCommandHandler ( "amiattached", consoleIsPlayerAttached )
```

See Also
--------
