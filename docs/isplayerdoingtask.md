Please use [isPedDoingTask](/docs/ispeddoingtask.md "wikilink")

This function checks if the specified player is carrying out a certain [task](/docs/list_of_player_tasks.md "wikilink").

Syntax
------

``` lua
bool isPlayerDoingTask ( player thePlayer, string taskName )
```

### Required Arguments

-   **thePlayer**: A [player](/docs/player.md "wikilink") object referencing the specified player.
-   **taskName**: A string containing the name of the [task](/docs/list_of_player_tasks.md "wikilink") you're checking for.

### Returns

Returns *true* if the player is currently doing the task, *false* otherwise.

Example
-------

This example checks if the player who entered the 'doingdriveby' command is doing a drive-by (clientside).

``` lua
function amIDoingADriveby ()
  if ( isPlayerDoingTask ( getLocalPlayer(), "TASK_SIMPLE_GANG_DRIVEBY" ) ) then
    outputChatBox ( getPlayerName ( getLocalPlayer() ) .. " is doing a driveby!!!" )
  else
    outputChatBox ( getPlayerName ( getLocalPlayer() ) .. " is not doing a driveby" )
  end
end
addCommandHandler ( "doingdriveby", amIDoingADriveby )
```

See Also
--------
