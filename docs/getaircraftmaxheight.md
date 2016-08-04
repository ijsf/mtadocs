This function gets the maximum height at which aircraft can fly without their engines turning off.

Syntax
------

``` lua
float getAircraftMaxHeight ( )
```

### Returns

Returns a float containing the max aircraft height.

Example
-------

<section name="Client" class="client" show="true">
This example returns the max aircraft height to a player if they use the command 'aircraftmaxheight'.

``` lua
function commandGetAircraftMaxHeight()
   local height = getAircraftMaxHeight() or "N/A"
   outputChatBox("Aircraft max height: "..height, 0, 255, 0)
end
addCommandHandler("aircraftmaxheight", commandGetAircraftMaxHeight)
```

</section>
See Also
--------
