This function is used to get the name of the current task of a certain type for a player.

Syntax
------

``` lua
string getPlayerTask ( player thePlayer, string priority, int taskType, [int index = 0] )
```

### Required Arguments

-   **thePlayer**: The [player](/player.md "wikilink") whose task you want to retrieve.
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

### Optional Arguments

-   **index**: An integer value representing how many sub tasks to go through. -1 to get the simplest task, 0 to get the most complex task.

### Returns

Returns a string containing the name of a task. See [list of player tasks](/list_of_player_tasks.md "wikilink") for valid strings. Returns *false* if invalid arguments are specified or if there is no task of the type or index specified.

Example
-------

<section name="Client" class="client" show="true">
This example prints the name of a player's task to the chat when they use the “task” command in the console.

``` lua
function myTask ( commandName, priority, taskType )
    task = getPlayerTask ( source, priority, tonumber(taskType) )
    taskName = "none"
    if ( task ) then
        taskName = task
    end
    outputChatBox ( getPlayerName( source ) .. "'s " .. priority .. "(" .. taskType .. ") task is: " .. taskName )
end    
addCommandHandler ( "task", myTask )
```

</section>
See Also
--------
