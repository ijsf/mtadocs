This function just adds a possibility to integrate a condition in e.g. some variable definition. It is as useful as simple. It's like the short “(c) ? t : f ;” statement that exists in e.g. PHP or JavaScript, or COALESCE in MySQL. It simulates a ternary operation.

*Note: This function is basically on the wiki to enable using it in other useful functions.*

Syntax
------

``` lua
var IfElse( bool condition, var trueReturn, var falseReturn )
```

### Required Arguments

-   **condition**: A condition like you could use it in an if-statement.
-   **trueReturn**: The value that should be returned if the condition is true.
-   **falseReturn**: The value that should be returned if the condition is false.

### Returns

Returns the second argument if condition is true, the third otherwise.

Code
----

<section name="Server- and/or clientside Script" class="both" show="true">
``` lua
function IfElse(condition, trueReturn, falseReturn)
    if (condition) then return trueReturn
    else return falseReturn end
end
```

</section>
Example
-------

<section name="Server" class="server" show="true">
This example adds a command to retrieve the actual player count.

``` lua
-- define the commandhandler function
function CmdPlayerCount(source)
    -- get the actual player count
    local playerCount = getPlayerCount()
    -- send message to the player
    outputChatBox("There "..IfElse(playerCount == 1, "is", "are").." actually "..playerCount.." Player"..IfElse(playerCount == 1, "", "s").." online.", source)
end
-- add the command handler
addCommandHandler("playerCount", CmdPlayerCount, false, false)
```

</section>
Author: NeonBlack

See Also
--------
