This function checks if the specified ped is carrying out a certain [task](/List_of_player_tasks.md "wikilink").

Syntax
------

``` lua
bool isPedDoingTask ( ped thePed, string taskName )
```

### Required Arguments

-   **thePed**: The [ped](/ped.md "wikilink") you want to check.
-   **taskName**: A string containing the name of the [task](/List_of_player_tasks.md "wikilink") you're checking for.

### Returns

Returns *true* if the player is currently doing the task, *false* otherwise.

Example
-------

This example checks if the player who entered the 'doingdriveby' command is doing a drive-by (clientside).

``` lua
function amIDoingADriveby ()
    if ( isPedDoingTask ( getLocalPlayer(), "TASK_SIMPLE_GANG_DRIVEBY" ) ) then
        outputChatBox ( getPlayerName ( getLocalPlayer() ) .. " is doing a driveby!" )
    else
        outputChatBox ( getPlayerName ( getLocalPlayer() ) .. " is not doing a driveby" )
    end
end
addCommandHandler ( "doingdriveby", amIDoingADriveby )
```

See Also
--------
