This resource was made off of the functions: [CallClientFunction](/CallClientFunction.md "wikilink") and [CallServerFunction](/CallServerFunction.md "wikilink")

Calling Functions
-----------------

<section name="callSF" class="client" show="true">
``` lua
 ) 
```

Required
========

-   **funcname**: The name of the function that should be called serverside. May also be a function in a table, e.g. “math.round”.

Optional
========

-   **agr1-argn**: The arguments that should be passed to the function.

Example
=======

This example removes the player from his team.

``` lua
-- get the local player element
local _local = getLocalPlayer()
-- define the leaveTeam command handler function
function cmdLeaveTeam()
    -- set the player's team to nil
    callServerFunction("setPlayerTeam", _local)
end
-- add the command handler
addCommandHandler("leaveTeam", cmdLeaveTeam, false)
```

</section>
<section name="callCF" class="server" show="true">
``` lua
 ) 
```

Required
========

-   **Client**: The element of the player who should be affected.
-   **funcname**: The name of the function that should be called serverside. May also be a function in a table, e.g. “math.round”.

Optional
========

-   **agr1-argn**: The arguments that should be passed to the function.

Example
=======

This example sets the player's minute duration.

``` lua
-- define the onPlayerJoin handler function
function onPlayerJoin()
    -- set the minute duration
    callClientFunction(source, "setMinuteDuration", 10000)
end
-- add the event handler
addEventHandler("onPlayerJoin", root, onPlayerJoin)
```

</section>
I give all thanks to Neon Black for making these functions.

See Also
--------

-   [Download](http://community.mtasa.com/index.php?p=resources&s=details&id=4858)
-   [callServerFunction](/callServerFunction.md "wikilink")
-   [callClientFunction](/callClientFunction.md "wikilink")
