Reversing GTA:SA code is the process of turning the x86 assembler instructions back into readable C++ code. It is made to fully understand logic inside of the GTA:SA engine. Results of code reversal can be put down as **assembler hooks** and/or **localized C++ implementations**.

Assembler Hooking
-----------------

This is the method MTA:BLUE developers use to provide features to the MTA runtime. When logic patterns have been analysed inside of the GTA:SA engine by careful study of the assembler instructions, manipulations to the assembler instructions can be made. This way the logical flow of engine code is tampered with. Changes are local to the game executable.

### Pros and Cons

| Pro                                      | Contra                                                                       | Neutral                                 |
|------------------------------------------|------------------------------------------------------------------------------|-----------------------------------------|
| -   Exploits of the engine stay hidden   
 -   Rockstar code is not shown to public  | -   Research is not shared with other developers                             
                                            -   Hackish agenda on an open source project                                  
                                            -   Only experts of their research can modify their hacks (elitist thinking)  
                                            -   Logic may not be compatible across multiple GTA:SA versions               | -   Cooperation of multiple GTA:SA mods |
||

''(The arguments are interpretations by The\_GTA.)

### Usage Explanation

While assembly hooks are not the optimal way to output research about the GTA:SA engine, they are very quick means to solve imminent problems of low complexity. For example, while it takes long to research the linked list container for the streaming garbage collection entity management, it takes less time to simply increase the amount of available nodes to be allocated. Hence assembly hooking is essential to prematurely provide features to the MTA runtime, while they may be reversed in the longrun. In that sense, it is not true that code that works should be left alone: assembly hooks are not proper coding and allow no optimizations to the logic they are targeting.

Localized C++ Implementations
-----------------------------

This is the way MTA:Eir developers use to provide features to the MTA runtime. First, the logic inside of the engine is analyzed. The researcher attempts to give meaning to said logic, by giving names to functions and variables that make sense. Once he thinks he fully understands the researched section of code, he rewrites the x86 assembler instructions into C++. Every researched function has to be given a comment header with a function description. The more a function is split into subroutines or the more patterns found have been put into shared functions, the better is the result of the research. Since the whole engine logic ties together, code research has to be revisited from time to time to make sure it is up to date in the context of the whole engine.

Changes to the original GTA:SA logic have to be marked with a comment that describes what has changed and where exactly. Additions which benefit the MTA runtime are often marked as “MTA extension”. Bugfixes to the engine have to be explained in a comment.

Since the rewritten version of code has to perfectly match the original GTA:SA logic, it is a very tiring and time-consuming process. But once the code has been completely reversed and **localized**, it is open for every developer to try his hands on it.

### What is Localization?

Localization is the process of extracting GTA:SA logic from its engine so that MTA can execute it stand-alone. It is required so that changes to the structures of GTA:SA can be made without breaking things. When code has been first rewritten the researcher is free to use the original GTA:SA binary offsets to reference structures and classes that he has found. This changes with Localization.

A binary offset is complex. It can be tied to many locations inside of the binary. Worst case scenario is if there are obfuscated references to the binary offset that cannot be spotted at development time but cause crashes during testing. It is mandatory to track all of the locations a memory address is referenced from, most notably using hardware breakpoints.

All routines that are tied to binary offsets have to be rewritten. Then groundbreaking changes can be made to the logic. If the logic is using a static pointer array natively, an improvement would be to introduce a linked list without limits. Target of such improvement is the GTA:SA rendering system, that lists to-be-rendered entities on a static pointer array and saves its count. A static array implies that rendering is limited to a certain count; this contradicts with a patch that introduces theoretically infinite entities into rendering. In this way, localization exposes contradicting or deprecated functionality.

When a system is completely reversed, it opens doors for **meta-programming**. Globals/macros that have been exposed can be modified to do performance tests of GTA:SA logic. Code can be split up into subroutines or turned into templates. New functionality can be added or existing functionality optimized by **common development theories** (multi-threading, fibers, complexity questions, fixing bottlenecks, ...).

### Localized implementations of MTA:Eir

-   streaming runtime, streaming loader, world sector streaming
-   IMG container management
-   vehicle rendering logic
-   RenderWare memory system
-   RenderWare renderstate system
-   Entity rendering queue

Sharing Research, and its problems
----------------------------------

Sharing code is a non-trivial activity of developer communities. It is tied to many problems, some of which are...

-   Code from other people is not understandable
-   Lack of trust to another persons research
-   Disliking another persons coding style
-   Lack of documentation
-   Not enough communication between developers

Addressing these issues is a tough task. Here are ways that they can be addressed.

### Code from other people is not understandable

-   ask the original developer
-   tell him to document certain regions of the code thoroughly
-   take some time to examine the code

### Lack of trust to another persons research

-   open a discussion with the community and the developer about your points
-   put yourself into the position of the developer and ask the questions to yourself
-   rate a developer by the work he is doing, the ideas he has

### Disliking another persons coding style

-   give improvement ideas about certain regions of code
-   ask him to follow the MTA coding guidelines

### Lack of documentation

-   give ideas to the developer how to document his code
-   if you understand it, discuss critical points with the developer
-   point him toward the MTA wiki

### Not enough communication between developers

-   ask developers to join \#mta.dev
-   bring up questions once in a while, even if they seem trivial
-   do not be afraid to be wrong, because the developer community as a whole is right

[Category: Development](/docs/category-_development.md "wikilink")
