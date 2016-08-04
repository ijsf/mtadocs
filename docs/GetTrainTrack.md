Syntax
------

``` lua
int getTrainTrack ( vehicle train )
```

### Required Arguments

-   **train:** the train of which to get the track.

### Returns

Returns an integer (whole number) that represents the train track, *false* if there is problem with train element.

Example
-------

``` lua
addCommandHandler("traintrack",
function (player)
   if isPedInVehicle (player) then
      local theVehicle = getPedOccupiedVehicle(player)
      if getVehicleType(theVehicle) == "Train" then
      local track = getTrainTrack(theVehicle)
      outputChatBox("Train Track is "..track,player,0,255,0)
      end
   end
end
)
```

See Also
--------
