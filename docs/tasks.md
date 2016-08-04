The task system is a system that is built into Grand Theft Auto: San Andreas. It is a large system that manages everything to do with how players and pedestrians behave. Every action a player or pedestrian performs is a task of some type. Each player can have a number of primary and secondary tasks. Primary tasks tend to be the most interesting to us when making scripts. Primary tasks are divided up into 5 slots ordered by priority, while secondary tasks are divided up into 6 slots each with a different purpose. The slots are as follows:

**PRIMARY TASKS**

-   **0:** TASK\_PRIORITY\_PHYSICAL\_RESPONSE
-   **1:** TASK\_PRIORITY\_EVENT\_RESPONSE\_TEMP
-   **2:** TASK\_PRIORITY\_EVENT\_RESPONSE\_NONTEMP
-   **3:** TASK\_PRIORITY\_PRIMARY
-   **4:** TASK\_PRIORITY\_DEFAULT

**SECONDARY TASKS**

-   **0:** TASK\_SECONDARY\_ATTACK
-   **1:** TASK\_SECONDARY\_DUCK
-   **2:** TASK\_SECONDARY\_SAY
-   **3:** TASK\_SECONDARY\_FACIAL\_COMPLEX
-   **4:** TASK\_SECONDARY\_PARTIAL\_ANIM
-   **5:** TASK\_SECONDARY\_IK

Each slot can contain one task at a time, or be empty.

There are two types of tasks - complex tasks and simple tasks. Simple tasks actually perform actions that affect the player, such as opening a car door, walking forwards etc. Complex tasks trigger off simple tasks in a sequence to perform more complex things, such as walking to a car, opening the door and getting in.

If a complex task is in a slot, you can get what task that complex task is running using [getPedTask](/docs/getPedTask.md "wikilink") and an index value of 1. If that itself has a child task, then you can retrieve that using an index value of 2 etc.

You can see a complete list of tasks on the [list of player tasks](/docs/list_of_player_tasks.md "wikilink") page. [Category:Scripting Concepts](/Category:Scripting_Concepts.md "wikilink")
