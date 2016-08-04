This function is used to get the name of a specified ped's current simplest [task](/docs/task.md "wikilink").
*Note: See [getPedTask](/docs/getpedtask.md "wikilink") to get a all tasks.*

Syntax
------

``` lua
string getPedSimplestTask ( ped thePed )
```

### Required Arguments

-   **thePed**: The [ped](/docs/ped.md "wikilink") whose [task](/docs/task.md "wikilink") you want to retrieve.

### Returns

Returns a string representing the name of the ped's simplest, active [task](/docs/task.md "wikilink").

Example
-------

This example prints the name of a player's simplest task to the chat, when they use the “sTask” command.

``` lua
function showSTask ()
  local thetask = getPedSimplestTask ( getLocalPlayer() )
  outputChatBox ( getPlayerName ( getLocalPlayer() ) .. "'s simplest task is: " .. thetask )
end
addCommandHandler ( "sTask", showSTask )
```

See Also
--------
