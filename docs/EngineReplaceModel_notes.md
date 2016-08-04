Replacing models in the original GTA map
========================================

There are two ways to replace models in the original GTA map:

Method 1: Move camera away during replace process
-------------------------------------------------

        local modelId = 12853

        setCameraMatrix( 10000, 0, 0 ) -- Move camera far away

        col = engineLoadCOL( "garage.col" )
        txd = engineLoadTXD( "garage.txd" )
        dff = engineLoadDFF( "garage.dff", 0 )
         
        engineReplaceCOL( col, modelId )
        engineImportTXD( txd, modelId )
        engineReplaceModel( dff, modelId )

        setTimer( function()
                    setCameraTarget( localPlayer ) -- Move camera back after a delay
                 end
                ,50,1 )

Method 2: Create custom object and hide original
------------------------------------------------

        local modelId = 12853
        local x,y,z = 661, -561, 17

        obj = createObject( modelId, x,y,z )
        removeWorldModel( modelId, 100, x,y,z ) -- Hide original

        col = engineLoadCOL( "garage.col" )
        txd = engineLoadTXD( "garage.txd" )
        dff = engineLoadDFF( "garage.dff", 0 )
         
        engineReplaceCOL( col, modelId )
        engineImportTXD( txd, modelId )
        engineReplaceModel( dff, modelId )

#### Additonal code if model has LOD:

If the model has a LOD version, that will need to be hidden:

        local modelIdLOD = 13245
        removeWorldModel ( modelIdLOD, 100, x,y,z ) -- Hide LOD

Optionally create a MTA LOD replacement so there is no hole in the map from a distance:

        -- This step is optional
        objLOD = createObject( modelIdLOD, x,y,z, 0, 0, 0, true )
        setLowLODElement(obj, objLOD)

And for extra points, add a custom dff for the MTA LOD replacement:

        -- This step is optional
        txdLOD = engineLoadTXD( "garageLOD.txd" )
        dffLOD = engineLoadDFF( "garageLOD.dff", 0 )
        engineImportTXD( txdLOD, modelIdLOD )
        engineReplaceModel( dffLOD, modelIdLOD )
