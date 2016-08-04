This event is triggered when a vehicle explodes.

Parameters
----------

No arguments

Source
------

The [source](/docs/event_system#Event_source.md "wikilink") of this event is the [vehicle](/vehicle.md "wikilink") that exploded.

Example
-------

**Example 1**

``` lua
vagosVehicle = nil

-- This will get called when the vagos vehicle explodes
function onVagosVehicleExplode ()
    outputChatBox ( "VAGOS VEHICLE DESTROYED!" )
end

-- This is called when THIS resource starts
function onThisResourceStart ()

    -- Create the vagos vehicle. A van.
    vagosVehicle = createVehicle ( 522, 0, 0, 5 )

    -- Add its explode handler. When this car explodes, onVagosVehicleExplode is called
    addEventHandler ( "onVehicleExplode", vagosVehicle, onVagosVehicleExplode )
end

--Add the resource start event
addEventHandler ( "onResourceStart", getResourceRootElement (), onThisResourceStart )
```

**Example 2:** This will show the name of any vehicle that blew up:

``` lua
function notifyAboutExplosion()
    -- source is the element that triggered the event and can be used in other events as well
    outputChatBox(getVehicleName(source) .. " just blew up")
end

-- by using getRootElement() as root, it works for any vehicle
addEventHandler("onVehicleExplode", getRootElement(), notifyAboutExplosion)
```
