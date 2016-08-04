Syntax
------

``` lua
float getTrainPosition ( vehicle train )
```

### Required Arguments

-   **train:** the train to get the position of

### Returns

Returns a float that represents how along the track it is, *false* if there is problem with train element.

Example
-------

<section class="server" name="Server script" show="true">
This example adds a command called "/getpos", allowing you to get the position of the train.

``` lua
function position(player)
  if player and isElement(player) then 
     if isPedInVehicle(player) then -- make sure we're actually in a vehicle
        local vehicle = getPedOccupiedVehicle(player)
      if vehicle then 
       local vehType = getVehicleType (vehicle) 
          if vehType == "Train" then -- make sure we're in a train
         local position = getTrainPosition (vehicle)
         outputChatBox("The Train position is: "..position)
          else
         outputChatBox("You are not in a train!")
          end
       end
    else
      outputChatBox("You are not in a vehicle!")
    end 
    end 
end
addCommandHandler("getpos",position)
```

</section>
See Also
--------
