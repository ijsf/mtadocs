The **RenderWare Plugin System** is an interface used to extend known RenderWare types. RenderWare structs are allocated in free lists which know the RenderWare struct size at runtime. One free list is created for every type which is to be extended. Management of RenderWare plugins is done through plugin container structs that hold **constructors**, **destructors** and **copy-constructors** of their plugin. Plugins can define stream **read** and **write** algorithms to save their properties to disk.

### Reference

-   **plugin struct** is the data structure which should be registered to the RenderWare type
-   **plugin object** is a RenderWare type with plugin support
-   **plugin container** is a global descriptor with extension information about the plugin object (such as size, constructors, destructors and stream callbacks)

Known RenderWare types with (built-in) plugin support
-----------------------------------------------------

-   **RpAtomic** - geometry rendering descriptor
-   **RpClump** - container of atomics, lights and cameras
-   **RpGeometry** - 3D mesh holder
-   **RpMaterial** - rendering material for geometry
-   **RpWorld** - sector manager for RenderWare scenes which handles dynamic lights
-   **RpLight** - dynamic light descriptor
-   **RwFrame** - matrix in 3d space which holds frame objects (atomics, lights, cameras), creates a hierarchy to transform and offset objects
-   **RwCamera** - viewport into 3d space with rendering properties
-   **RwRaster** - gfx texture data
-   **RwTexture** - raster rendering descriptor
-   **RwTexDictionary** - container of textures to look-up by name

Registration of plugin object extensions
----------------------------------------

Each plugin object (that is one of the above RenderWare types) offers a **plugin registration routine**. It registers plugin struct details into the **plugin container**. It is defined as follows...

### RwObjectRegisterPlugin

`size_t RwObjectRegisterPlugin( size_t sPluginSize, unsigned int uiPluginID, RwPluginConstructor constructor,`
`RwPluginDestructor destructor, RwPluginCopyConstructor copyConstructor = NULL );`

-   **sPluginSize** - size of the plugin struct which is to be registered at the plugin object
-   **uiPluginID** - unique ID of the plugin so it can be recognized by the system (e.g. in streams)
-   **constructor** - called upon plugin object construction to set up plugin struct at it's offset
-   **destructor** - called upon plugin object destruction to release associated resources
-   **copyConstructor** (can be NULL) - called upon plugin cloning to recreated properties of the source plugin object in the new one with same properties

The function returns the offset of the registered plugin struct.

### Callback types (templates)

#### RwPluginConstructor

`template `<class objectType>
`objectType* RwPluginConstructor( objectType *obj, size_t sPluginOffset );`

#### RwPluginDestructor

`template `<class objectType>
`void RwPluginDestructor( objectType *obj, size_t sPluginOffset );`

-   **obj** - plugin object in question
-   **sPluginOffset** - offset of the plugin struct

If the constructor routine returns NULL, the plugin has failed to construct. It is not recommended to do so, since the plugin object will be given to the runtime anyway. On the other hand, the destructor must not fail.

#### RwPluginCopyConstructor

`template `<class objectType>
`objectType* RwPluginCopyConstructor( objectType *objNew, objectType *source, size_t sPluginOffset );`

-   **objNew** - the newly created plugin object
-   **source** - plugin object to clone data from
-   **sPluginOffset** - offset of the plugin struct

Registration of plugin object stream extensions
-----------------------------------------------

Plugin structs may offer a stream representation. Once sections designated by the struct id are found in a RwStream, the **read callback** is issued. If a RenderWare type is written to disk, all **write callback**s are invoked. Plugins do not have to write details to disk. The registration routine is defined as follows...

### RwObjectRegisterPluginStream

`size_t RwObjectRegisterPluginStream( unsigned int uiPluginID, RwPluginStreamRead readCallback, RwPluginStreamWrite writeCallback,`

RwPluginStreamGetSize sizeCallback );

-   **uiPluginID** - id of the plugin struct (to find it in the registry)
-   **readCallback** - issued once a plugin struct is found by id in the RwStream
-   **writeCallback** - invoked once a plugin object is written to RwStream
-   **sizeCallback** - called to return the size of the plugin struct in the stream (for allocation purposes)

The plugin struct offset is returned if successfully registered. Otherwise the function returns 0 (which is always an invalid offset). The registration will fail if the plugin struct has not been registered previously. Therefor call RwObjectRegisterPlugin before RwObjectRegisterPluginStream!

### Callback types (templates)

#### RwPluginStreamRead

`template `<class objectType>
`RwStream* RwPluginStreamRead( RwStream *stream, size_t sPluginSize, objectType *obj );`

-   **stream** - source stream of the plugin object
-   **sPluginSize** - size of the plugin object (returned from RwPluginStreamGetSize)
-   **obj** - plugin object to write data to

If this function succeeds, it should return the stream. Otherwise it can return NULL. This means that reading the RenderWare type has failed. The runtime will receive a NULL pointer then.

#### RwPluginStreamWrite

`template `<class objectType>
`int RwPluginStreamWrite( RwStream *stream, size_t sPluginSize, objectType *obj );`

-   **stream** - source stream of the plugin object
-   **sPluginSize** - size of the plugin object (returned from RwPluginStreamGetSize)
-   **obj** - plugin object to write data to

This callback should return a boolean whether writing succeeded or not.

#### RwPluginStreamGetSize

`template `<class objectType>
`size_t RwPluginStreamGetSize( objectType *obj );`

-   **obj** - plugin object to write to disk

This callback should return the required size to write to the RwStream. If 0 is returned, no data has to be written to disk (hence no section is created). The return value is passed to the write callback.

Lifetime of a RenderWare plugin object
--------------------------------------

Once a plugin object is created, first it is filled with RenderWare data. Then all constructors are called in their assignment order to fill all plugin details. To access plugin details, API has to be created which accesses the plugin struct (which has been registered at said plugin) at the offset it is assigned to. Usually there is a global variable which holds the plugin struct offset that is used in all API. Since the structs are constructed the same way all the time, the plugin struct offset information could be omitted by creating a new definition which maps out the offsets statically at compile-time. Optimal implementations use the plugin struct offset returned by the registration function, so that each registered struct in the plugin object is independent from others.

On destruction, all plugin structs are destroyed by calling their destructors in reverse assignment order.

[category:GTA Games](/docs/category:gta_games.md "wikilink")
