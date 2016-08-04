This function returns a table containing the valid (drivable) vehicles for GTA:SA

Syntax
------

``` lua
table getValidVehicleModels (  )
```

### Returns

Returns a table with the MTA vehicle models.

Code
----

``` lua
function getValidVehicleModels ( )
    local validVehicles = { }
    local invalidModels = {
        ['435']=true, ['449']=true, ['450']=true, ['537']=true,
        ['538']=true, ['569']=true, ['570']=true, ['584']=true,
        ['590']=true, ['591']=true, ['606']=true, ['607']=true, 
        ['608']=true
    }
    for i=400, 609 do
        if ( not invalidModels[tostring(i)] ) then
            table.insert ( validVehicles, i )
        end
    end
    return validVehicles
end
```

Example
-------

This is an example of the function.

``` lua
for index, model in ipairs ( getValidVehicleModels ( ) ) do
    outputChatBox ( tostring ( model ) ) 
end
```

Author: xXMADEXx

See Also
--------
