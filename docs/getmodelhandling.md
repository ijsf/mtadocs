This function returns a table containing the handling data of the specified vehicle model.

Note: the data returned may not reflect the actual handling of a particular vehicle, since this may be overriden by the [setVehicleHandling](/docs/setvehiclehandling.md "wikilink") function.

Syntax
------

``` lua
table getModelHandling ( int modelId ) 
```

### Required Arguments

-   **modelId:** the vehicle model you wish to get the handling data of.

### Returns

Returns a *table* containing all the handling data, *false* if an invalid vehicle model is specified. Here is a list of valid table properties and what they return:

Example
-------

<section name="Server" class="server" show="true">
``` lua
function getHandlings(thePlayer,commandName,id) 
   if id then
     local getVehicleHandlings = getModelHandling(id) 
        for k in pairs (getVehicleHandlings) do 
           outputChatBox(tostring(k)) 
        end
   else return end 
end
addCommandHandler("gethandling",getHandlings)
```

</section>
See other vehicle functions
---------------------------
