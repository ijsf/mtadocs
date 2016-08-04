This function gets the model name of an object model from model ID.

Syntax
------

``` lua
string engineGetModelNameFromID ( int modelID )
```

### Required Arguments

-   **modelID:** The model ID of the object

### Returns

Returns a *string* with the name of the object model, false otherwise.

Example
-------

This example gets the model name of an element you target (doesn't work for San Andreas world)

``` lua
function getTargetModelName(target) 
    if ( isElement(target) and getElementType(target) == "object" ) then 
        outputChatBox(tostring(engineGetModelNameFromID(getElementModel(target))))
    end
end
addEventHandler("onClientPlayerTarget", localPlayer, getTargetModelName)
```

See Also
--------
