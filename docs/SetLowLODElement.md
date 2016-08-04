This function assigns a low LOD element to an element. The low LOD element is displayed when its associated element is not fully visible. If a low LOD element is assigned to several elements, it will be displayed when any of these elements are not fully visible.

Syntax
------

``` lua
bool setLowLODElement ( element theElement, element lowLODElement )
```

### Required Arguments

-   **theElement:** The [element](/element.md "wikilink") whose low LOD version we want to change.
-   **lowLODElement :** A low LOD element to display when the first element is not fully visible.

### Returns

Returns *true* if the assignment was successful, *false* otherwise.

Example
-------

### Example 1

<section name="Clientside" class="client" show="true">
This example shows how to create and link a normal and low LOD object:

``` lua
    -- Create an normal object
    objNormal = createObject ( 3620, x,y,z,0,0,0 )

    -- Create a low LOD object
    objLowLOD = createObject ( 5154, x,y,z,0,0,0,true )

    -- Set the normal object low LOD version
    setLowLODElement ( objNormal, objLowLOD )

    -- Set the draw distance for the model we are using for low LOD to maximum
    engineSetModelLODDistance ( 5154, 300 )
```

</section>
### Example 2

<section name="Serverside" class="server" show="true">
This example shows how to create and link a composite object

``` lua
    -- Create composite object
    objMainBit = createObject ( 3620, x,y,z )
    objLeftBit = createObject ( 5158, x,y,z )
    objRightBit = createObject ( 5158, x,y,z )
    objDetailBit1 = createObject ( 1337, x,y,z )
    objDetailBit2 = createObject ( 1337, x,y,z )
    objInternalBit = createObject ( 1337, x,y,z )
    attachElements ( objLeftBit, objMainBit, -10, 0, 0 )
    attachElements ( objRightBit, objMainBit, 10, 0, 0 )
    attachElements ( objDetailBit1, objMainBit, 5, 0, 0 )
    attachElements ( objDetailBit2, objLeftBit, 5, 5, 0 )
    attachElements ( objInternalBit, objRightBit, 5, 7, 0 )

    -- Create low LOD object (which represents the whole composite model)
    objlowLOD = createObject ( 5154, x,y,z, 0, 0, 0, true )

    -- Attach low LOD object so it moves with the main model
    attachElements ( objlowLOD, objMainBit, 0, 0, 0 )

    -- Set associations so the low LOD model is displayed when the main parts are not full visible
    setLowLODElement ( objMainBit, objlowLOD )
    setLowLODElement ( objLeftBit, objlowLOD )
    setLowLODElement ( objRightBit, objlowLOD )

    -- Note that the detail and internal parts have not been associated to the low LOD object

    -- Set the draw distance for the model we are using for low LOD to maximum
    triggerClientEvent("onClientChangeModelLODDistance", resourceRoot, 5154, 300 )
```

</section>
<section name="Clientside" class="client" show="true">
Changing the draw distance for a model has to be done on the client:

``` lua
addEvent("onClientChangeModelLODDistance",true)
addEventHandler("onClientChangeModelLODDistance", resourceRoot,
    function(model,distance)
        engineSetModelLODDistance ( model, distance )
    end
)
```

</section>
Requirements
------------

See Also
--------
