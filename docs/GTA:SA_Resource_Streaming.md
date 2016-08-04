The **GTA:SA Resource Streaming system** loads data from disk into game memory. It is divided into IMG container management, threaded resource reading, conversion into engine objects, COL/IPL sector loading and game logic. It has been created to **asynchronously load resources**.

Known resource types
--------------------

| Name                        | ID range    | Description                                                                                                                                                                                               |
|-----------------------------|-------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Models (.DFF)               | 0-19999     | All game models are in these IDs. Internally this range is further split up into subsections of objects, vehicles and peds.                                                                               |
| Texture Dictionaries (.TXD) | 20000-24999 | Contains texture dictionary slots. Texture dictionaries are containers with all game textures. The game assigns texture dictionaries to models.                                                           |
| Collision Sectors (.COL)    | 25000-25255 | Slots holding all loaded collision sectors. Collision sectors are COLL containers that can be referenced and stretch across in-game bounds (based on buildings that use them).                            |
| IPL Sectors (.IPL)          | 25256-25510 | Slots holding all loaded IPL sectors. IPL sectors are represented by the binary .ipl files inside of the .IMG container. The game loads them inside of its bounds, only when they are required.           |
| Pathnode Containers (.DAT)  | 25511-25574 | Pathnodes are aligned in 8\*8 sectors of 750\*750 units. When the game references such a quad, it loads the associated pathnode files, that are numbered after the (height \* rowLen + rowIndex) formula. |
| Animation Blocks (.IFP)     | 25575-25754 | Animation blocks contain all animation sequences. Models can reference animation blocks, so they request them along.                                                                                      |
| Recordings (.RRR)           | 25755-25819 | Recordings hold prerecorded game motion data. This motion data is used during missions when you have to chase somebody or drive-by against enemies while a friend is driving.                             |

Description
-----------

### IMG Container Management

During engine initialization, the game loads configuration files that tell it which .IMG containers to use. When the Streaming system initializes, it attempts to load the registered .IMG containers. Every .IMG container is referenced using an unique index inside of a IMGFile array. The game keeps the .IMG container file handles open so it can constantly read from them.

When an .IMG container is being loaded, every file can represent a new resource ID inside of the engine (CModelInfoSA structure). **Models** get the IDs by matching their filename against an .IDE entry. If none is found, the engine maintains a small resource cache. These resources can still be loaded using RequestSpecialModel. **Texture Dictionaries** obtain a new ID. There is a hard-coded limit of 5000 TXDs. **COLL** and **IPL** sectors also obtain a new ID based on loading order. All the remaining resources go along with the same principle.

The internal CModelInfoSA array represents each resource entry in .IMG files. The engine supports 26310 resource IDs in total.

#### Possible resource loading statuses

| Name               | Description                                                                                                                                |
|--------------------|--------------------------------------------------------------------------------------------------------------------------------------------|
| MODEL\_UNAVAILABLE | The resource has not been loaded yet. No game resource is loaded for this entry. This resource is not used by any part of the game engine. |
| MODEL\_LOADED      | This resource has been loaded by the Streaming system. It is ready to be used by the game engine.                                          |
| MODEL\_LOADING     | This resource resides on the to-be-loaded queue. It waits to be picked up by the Streaming system for reading from disk.                   |
| MODEL\_QUEUE       | A slicer is currently reading data from disk for this resource.                                                                            |
| MODEL\_RELOAD      | This resource is currently being loaded in coroutine fashion. Data that is associated with it is too big to be loaded in one go.           |

[960px](/docs/File:Res_loader_sys.png.md "wikilink")

### (Threaded) Resource Reading

There is an entirely separate system just for reading data chunks from disk, known as the **streaming runtime**. The game can create **stream handles** to files on disk. By calling the **ReadStream** function, an asynchronous request to read data from a stream handle is made. Reading activity is maintained in **syncSemaphore** structures that hold internal data about the reading process (like file handle or OVERLAPPED structure). Calling **GetSyncSemaphoreStatus** with the syncSemaphore index as argument will return the request status (i.e. reading has finished). **CancelSyncSemaphore** stops any asynchronous request.

During start-up, the system checks the capabilities of the system. By default, **threading is enabled**. A read from GTA3.IMG is attempted using overlapped I/O to check for its support. The system will select the best compatible configuration. On modern machines, this means threading with overlapped I/O. In a worst case scenario, the game reads data synchronous on a single thread which halts game execution if data is read from slow storage media.

### Conversion into Engine Objects

The Streaming system natively maintains two reading slicers. A reading slicer checks which requested data is close in an .IMG container and reads multiple data in one go. Using modification of the logic the engine can support an arbitrary number of slicers, that all share chunks inside of a reading buffer. The more slicers, the smaller the reading buffer section for each. If data that is read does not fit into a single slicer, the Streaming system waits for all smaller requests to finish and then reads that big data on the first slicer using the whole reading buffer. The reading buffer size is determined by the biggest resource inside any registered .IMG container.

There are **4 states** that a **slicer** can be in: idle, buffering, loading and waiting. Idle slicers wait for requests that can occupy them. When slicers are buffering, they wait for their read requests to finish. Loading slicers wait until the game has loaded all game resources from them. Waiting is an exceptional status that is caused if a slicer is requested to push data for engine object conversion but the read requests have not finished yet.

Loading is the most interesting status. The slicers push the raw data into loader routines along with their model IDs. Using the **model ID** the engine knows what that raw data is supposed to represent. For instance, model id 1361 is a model resource that is stored in a .DFF file. The loader routines usually load data in one go. If data is found too big, it can be **loaded across multiple slicer pulses** (the slicer resides in **loading status**). Then the data is processed in **coroutine fashion**. Natively, only **texture dictionaries** that exceed a certain block count use this feature. Also, the engine has been optimized to assume that all data is loaded in two slicer pulses (max.).

Each slicer has its own **syncSemaphore** from the streaming runtime. The syncSemaphore index corresponds to the slicer index.

### COL/IPL Sector Loading

The GTA:SA engine maps COLL and IPL sectors to world coordinate boundaries. When the streaming position (natively the player position) intersects with any sector, it will be requested to load. This activity is maintained in the **Sectorizer** template class. Every COLL and IPL sector is added into a quad tree to boost world area look-up. Sectors are allocated from a private data pool. Sectors have their own manager that specializes the Sectorizers activity (loading and unloading, pool index to model id conversion, sector marking logic).

### Game Logic

When the camera is close to the ground, the Streaming system pulses game activity management. Game activity is pre-loading of event models and streaming of event zones. These features have been disabled in MTA, but are interesting if SP support is considered.

Multiplayer Support
-------------------

MTA:SA sets high demands for the GTA:SA engine. The streaming system was meant to be the central location to load resources from. Hence, natively, the system does not expect interaction of outside sources, such as the MTA runtime.

To fix this problem, the entire system has to be understood and properly expanded. The **RequestModel** function and the **FreeModel** function are used to request resources for every game instance. By expanding the logic of these functions, MTA can offer custom resources to the game engine (i.e. models and collisions). Simple ASM hooks are insufficient, as the code requires heavy adjustments which need to be clear to every MTA developer. For instance, to prevent memory leaks and instability, the Streaming **slicer** activity and the loader queue have to be adjusted according to how MTA manipulates the resource status.

In MTA:Eir, the model support has been fixed by offering model resources on base model info request and preventing the deletion of custom collisions when COL sectors are being unloaded.

Ideas for Expansion
-------------------

Natively, the loader does not operate with perfect efficiency. As stated above, the system mimicks coroutine behavior. If very big .DFF models are loaded, the Streaming system can cause FPS drops. The way texture containers are loaded is imperfect, even if their loading is split into two pulses. The theory is that the conversion of every texture into a game instance is a complex task. Natively, streaming is not dependant on timing of the load process. If it were, then the system could yield when a TXD container takes too long to load.

My proposal is that every slicer obtains a fiber in a MTA execution manager. Once per frame (and at all other plausible moments) all fibers will be pulsed, thus progressing resource loading. Since every fiber maintains its own runtime stack, complex code is avoided. When a certain quota of data is read from a RenderWare stream, the fiber's execution is yielded. Such a change in resource loading is going to smoothen the FPS of GTA:SA when traveling across the world.

Problem with such a proposal is that the RenderWare streaming functions are hooked by the network module.

### Fibered Loading

This is a technique utilized in MTA:Eir to improve the performance of low-end computers. It generally smoothens the FPS count of the game by removing lag-spikes. In native GTA:SA, resources are mostly loaded in one go. Using [fibered loading](/docs/MTA:Eir/functions/engineStreamingSetFiberedLoadingEnabled.md "wikilink") on the other hand, loading of resources depends on the time the Streaming system may take per frame. The time it may take is derived from the total execution time of last frame.

Imagine that a very big TXD container is stored inside of GTA3.IMG. Such resources take a relatively long time to be buffered into game memory and an initialization attempt during Streaming loading may cause a lagspike, since much data is processed at once. If fibered loading is enabled, a coroutine (a.k.a. fiber) is created for every resource loading *slicer* with its own execution stack. When the loader attempts to read resources from the buffer, the fiber executive manager checks whether the fiber has taken [its time](/docs/MTA:Eir/functions/engineStreamingSetFiberedPerfMultiplier.md "wikilink") already. If so, it yields during the read process. Execution will continue next game frame.

[ru:GTA:SA\_Resource\_Streaming](/docs/ru:GTA:SA_Resource_Streaming.md "wikilink") [Category: Development](/Category:_Development.md "wikilink")
