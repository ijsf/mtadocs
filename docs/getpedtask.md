This function is used to get any simple or complex [task](/docs/task.md "wikilink") of a certain type for a ped.

It can provide feedback on all tasks relating to a ped. For example, while jumping, [getPedSimplestTask](/docs/getpedsimplesttask.md "wikilink") will return TASK\_SIMPLE\_IN\_AIR. If you wanted to know specifically if the player has jumped, you would use this function. If you did you will discover that while jumping Primary task 3 is TASK\_COMPLEX\_JUMP.

Syntax
------

``` lua
string, string, string, string getPedTask ( ped thePed, string priority, int taskType )
```

### Required Arguments

-   **thePed**: The [ped](/docs/ped.md "wikilink") whose task you want to retrieve.
-   **priority**: A string determining which set of tasks you want to retrieve it from. This must be either “primary” or “secondary”.
-   **taskType**: An integer value representing the task type (or slot) you want to get the task from. Types can be:
    -   **PRIMARY TASKS**
        -   **0:** TASK\_PHYSICAL\_RESPONSE
        -   **1:** TASK\_EVENT\_RESPONSE\_TEMP
        -   **2:** TASK\_EVENT\_RESPONSE\_NONTEMP
        -   **3:** TASK\_PRIMARY
        -   **4:** TASK\_DEFAULT
    -   **SECONDARY TASKS**
        -   **0:** TASK\_SECONDARY\_ATTACK
        -   **1:** TASK\_SECONDARY\_DUCK
        -   **2:** TASK\_SECONDARY\_SAY
        -   **3:** TASK\_SECONDARY\_FACIAL\_COMPLEX
        -   **4:** TASK\_SECONDARY\_PARTIAL\_ANIM
        -   **5:** TASK\_SECONDARY\_IK

### Returns

Returns the name of the most complex task. See [list of player tasks](/docs/list_of_player_tasks.md "wikilink") for valid strings. Returns *false* if invalid arguments are specified or if there is no task of the type specified.

Example
-------

This example draws the active primary and secondary tasks (including task hierarchy in 1.1) as your local player moves around the world.

``` lua
function displayMyTask ()
    local x,y = 100,200
    for k=0,4 do
        local a,b,c,d = getPedTask ( getLocalPlayer(), "primary", k )
        dxDrawText ( "Primary task #"..k.." is "..tostring(a).." -> "..tostring(b).." -> "..tostring(c).." -> "..tostring(d).." -> ", x, y )
        y = y + 15
    end
    y = y + 15
    for k=0,5 do
        local a,b,c,d = getPedTask ( getLocalPlayer(), "secondary", k )
        dxDrawText ( "Secondary task #"..k.." is "..tostring(a).." -> "..tostring(b).." -> "..tostring(c).." -> "..tostring(d).." -> ", x, y )    
        y = y + 15
    end
end    
addEventHandler ( "onClientRender", root, displayMyTask )
```

See Also
--------
