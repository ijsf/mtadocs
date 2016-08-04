This function detaches attached elements from one another.

Syntax
------

``` lua
bool detachElementFromElement ( element theElement, [ element theAttachToElement ] )
```

### Required Arguments

-   **theElement:** The element to be detached (the “child”)

### Optional Arguments

-   **theAttachToElement:** The element you wish to detach from, will detach from the attached element if this isn't specified.

### Returns

Returns *true* if the detaching was successful, *false* otherwise.

Example
-------

**Example 1:** This example attaches a marker to a vehicle, and detaches it when it blows up:

``` lua
function attachMarkerToVehicle ( theVehicle )
    -- create the marker to attach
    local arrowMarker = createMarker ( 0, 0, 0, "arrow", 1.5, 0, 0, 255, 255 )
    -- attach the marker above the vehicle
    attachElementToElement ( arrowMarker, theVehicle, 0, 0, 2 )
    -- add an event handler for when the vehicle blows up
    addEventHandler ( "onVehicleExplode", theVehicle, "onMarkedCarExplode" )
end

function onMarkedCarExplode ()
    -- get the elements attached to the vehicle
    local attachedElements = getAttachedElements ( source )
    -- loop through the table of elements
    for i,v in ipairs ( attachedElements ) do
        -- detach the element from the vehicle
        detachElementFromElement ( v, source )
    end
    -- remove the event handler
    removeEventHandler ( "onVehicleExplode", source, "onMarkedCarExplode" )
end
```

**Example 2:** This function will detach any elements that might have been attached to the passed element:

``` lua
function freeElement( theElement )
      if ( isElementAttached( theElement ) ) then --If the specified element is attached to something
            detachElementFromElement( theElement ) --Detach it.
      else
            outputChatBox( "Element is not attached" ) --If not, say it wasn't attached in the first place.
      end
end
```

See Also
--------
