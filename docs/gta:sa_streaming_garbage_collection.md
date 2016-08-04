The **GTA:SA Streaming Garbage Collection system** monitors the usage of game memory. It maintains the streaming memory limit for the entire game engine. Streaming memory is calculated by adding up the resource file chunk size of every loaded game resource. When the limit is reached, the system will attempt to free space by destroying resources from game instances. If this process fails, the game engine will hang (by design). This limit can be adjusted by setting the video memory setting in your MTA video settings.

Active Streaming Entities
-------------------------

[200px|thumb|right|Full potencial of GTA:SA streaming.](/docs/File:chillahad_farclip.png.md "wikilink") Objects, buildings and dummies that have their RenderWare resources loaded are added into the **active entity garbage collector**. Once it runs, it will destroy the RenderWare objects of all registered entities that are **out of sight** and **far away**. If the model reference count has reached 0, the system will free the model resource. Natively, the engine can **handle 1000 entities** in its sorted container (CRenderChainInterface <streamingChainInfo>). If allocation of a container node fails, the requesting entity does destroy its RenderWare data. Hence, natively, only 1000 objects, buildings or dummies can be rendered at a time. The failure to allocate container nodes has often been seen at high draw distances (a.k.a. the **blinking building bug**).

The MTA developer [ccw](/docs/user:ccw.md "wikilink") is the person who first found the blinking building bug.

### Node Allocation Methods

There are multiple ways to allocate streaming nodes when they are not available anymore. Natively, the GTA:SA engine **steals streaming nodes** from the first entities it finds on the streaming garbage collection entity registry. This is why **the world flickers wildly** when it is out of available nodes.

A better way is to **garbage collect the world on demand**. This way only entities that are out of sight will lose their RenderWare data. The performance of this method depends on the nature of the registered streaming GC entities as well as the amount of registered entities.

If memory and GPU performance is not of concern, the engine can **allocate new nodes into the system** so that more entities can have their RenderWare data allocated on the world. This results in **theoretically infinite entities visible** on the screen.

While each method has its strong and weak points, the optimal way to stream the world is to **switch between these methods at runtime**. MTA:Eir will ship with a standard **streaming\_opt** resource that will do this for you. The plan is that streaming nodes will be allocated depending on engine performance and demand.

Implementation differences between MTA versions
-----------------------------------------------

### MTA:BLUE

The draw distance bug has been decimated in MTA:BLUE. The maximum number of managed streaming entities has been increased to 2500 to compensate for large drawing distances. That increases the engine performance a lot, as more streaming memory can be allocated by game entities.

### MTA:Eir

In MTA:Eir, the drawing distance bug has been fixed, too. While the hardcoded maximum has been left at 1000 entities inside of the garbage collection system, when the limit has been reached, the system allocates new nodes into the sorted container. There is theoretically no limit to object, dummy and building streaming this way.

Multiple options have been added through scripting functions to change the streaming node allocation behavior. The flickering is no longer a bug, but a feature that can be disabled. Using [scripting functions](/docs/MTA:Eir/New_Scripting_Functions.md "wikilink") Lua scripts can retrieve the amount of nodes allocated and free to be allocated.

References
----------

-   <http://gtaforums.com/topic/573478-iiivcsa-project-2dfx> - pioneers of draw distance fixing

[ru:GTA:SA\_Streaming\_Garbage\_Collection](/docs/ru:GTA:SA_Streaming_Garbage_Collection.md "wikilink") [Category: Development](/Category:_Development.md "wikilink")
