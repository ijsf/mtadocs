The **GTA:SA rendering system** is a **high-level render object management** based on the RenderWare SDK and Direct3D 9.

Entity Rendering
----------------

Every game frame the engine loops through all **streamed-in entity sectors** and builds up the rendering context based on every single entity it finds. The entities are processed by their **type** (building, vehicle, ped, object, dummy), their **effective position** (underwater, on ground, on/off screen) and **game configuration** (model flags, handling flags).

As a result, multiple rendering lists are filled: sorted on ground, sorted underwater, sorted 'grasshouse' models, static array on-ground, static array level-of detail, static array out-of-sight low-priority.

### Alpha Issues

Due to the nature how GTA:SA renders its entities, several alpha issues crop up through-out the entire rendering stage. It starts with the fact that each rendering stage is not **alpha-compatible** to another. If alpha models render on two separate render stages, they will bug on certain camera angles if looking through either one. Another discomfort is that alpha through alpha is badly implemented on a per-model basis, leaving look-through artifacts when looking at trees or fences in certain places on the GTA:SA map.

There is no performant ultimative fix for the whole GTA:SA scene. The issues can be combated in [multiple ways](/docs/mta-eir/functions/enginesetworldrendermode.md "wikilink"). The **meshlocal\_alphafix** method implements 'alpha fixing' on a per-mesh basis for objects and peds, so that leaves on a tree can be layered without limitation. The **scene\_alphafix** method reorders the GTA:SA entity rendering queues so that they conform to **alpha rendering rules**.

Each of these methods follows simple **alpha rendering rules**. Opaque pixels are drawn first so they occlude pixels behind them and unnecessary blending operations are avoided. Then **translucent** pixels are drawn in reverse order to the opaque elements, the most distant element being drawn first and the closest one last. In the end, the depth is written for each translucent pixel so that different rendering stages do not conflict with the already drawn pixels.

These fixes are nowhere perfect. Perfect render ordering of alpha pixels is not determined but luck-based. Depth across rendering stages is conflicting for alpha pixels.

Rendering Callbacks
-------------------

The GTA:SA RenderWare implementation uses pipelines that can process implementation based requests. The most common request is the **rendering of an atomic**. With each pipeline there is a unique rendering callback associated with it. These callbacks implement special rendering functionality that is available to different GTA:SA engine model infos.

The **ReflectiveRenderCallback** is used to render entities that may have reflective maps attached to their materials. A reflective map is a **texture that is rendered as a billboard toward the camera** on the surface of the atomic.

The **SpecialObjectRenderCallback** is used to render entities in a similar way to **ReflectiveRenderCallback**. The actual rendering output is the same, but certain parameters are used differently.

The **VehicleAtomicRenderCallback** is used to render all kinds of vehicle atomics. A reflective map can be attached to either one using the method described in **ReflectiveRenderCallback**. A special rendering method is added that renders a cubic environment map around an atomic, creating the illusion of reflection.

[Category: Development](/docs/category-_development.md "wikilink")
