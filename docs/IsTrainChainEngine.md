Syntax
------

``` lua
bool isTrainChainEngine ( vehicle theTrain )   
```

### Arguments

-   **theTrain:** a [train](/Element/Vehicle.md "wikilink") to check if it's a chain engine or not.

### Returns

-   *true* if a [train](/Element/Vehicle.md "wikilink") was passed to the function and if it's a chain engine.
-   *false* otherwise.

Example
-------

The next code snippet adds a /isthistrainachainengine, which checks if the train occupied by the player who types the command is a chain engine or not.

``` lua
function checkTrainChainEngine()
   if isPedInVehicle(localPlayer) then
      local train = getPedOccupiedVehicle(localPlayer)
      if getVehicleType(train) == "Train" then
     outputChatBox("Your train " .. (isTrainChainEngine(train) and "is" or "isn't") .. " a chain engine.", 255, 128, 0)
      else
     outputChatBox("You need to be in a train to use this command.", 255, 0, 0)
      end
   end
end
addCommandHandler("isthistrainachainengine", checkTrainChainEngine)
```

See also
--------

[ru:IsTrainChainEngine](/ru:IsTrainChainEngine.md "wikilink")
