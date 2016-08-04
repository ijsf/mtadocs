This function checks if a vehicle is damage proof (set with [setVehicleDamageProof](/setVehicleDamageProof.md "wikilink")).

Syntax
------

``` lua
bool isVehicleDamageProof ( vehicle theVehicle )
```

### Required Arguments

-   **theVehicle:** the vehicle whose invincibility status we want to check.

### Returns

Returns *true* if the vehicle is damage proof, *false* if it isn't or if invalid arguments were passed.

Example
-------

This example will output in the chatbox whether the vehicle is vulnerable to damage or not when a player enters in it.

``` lua
function checkVulnerability(theVehicle)
   if isVehicleDamageProof(theVehicle) == true then
            outputChatBox("This vehicle is not vulnerable to damage", source)
   else
            outputChatBox("This vehicle is vulnerable to damage", source)
   end
end
addEventHandler ( "onPlayerVehicleEnter", getRootElement(), checkVulnerability )
  
```

See Also
--------
