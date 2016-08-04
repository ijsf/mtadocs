This function is used to get the name of a specified players current simplest [task](/task.md "wikilink").
**DP2 note:** Don't call this on players that have not spawned. This will crash the client.

Syntax
------

``` lua
string getPlayerSimplestTask ( player thePlayer )
```

### Required Arguments

-   **thePlayer**: The [player](/player.md "wikilink") whose [task](/task.md "wikilink") you want to retrieve.

### Returns

Returns a string representing the name of the player's simplest, active [task](/task.md "wikilink").

Example
-------

This example prints the name of a players simplest task to the chat, when they use the “sTask” command.

``` lua
function showSTask ()
  local thetask = getPlayerSimplestTask ( getLocalPlayer() )
  outputChatBox ( getPlayerName ( getLocalPlayer() ) .. "'s simplest task is: " .. thetask )
end
addCommandHandler ( "sTask", showSTask )
```

See Also
--------
