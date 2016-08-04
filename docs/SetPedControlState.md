This function makes a [ped](/ped.md "wikilink") press or release a certain control. It doesn't work with the local player, so use [setControlState](/setControlState.md "wikilink") instead.

Syntax
------

``` lua
bool setPedControlState ( ped thePed, string control, bool state )
```

### Required Arguments

-   **thePed:** the ped you want to press or release a control.
-   **control:** the name of the control of which to change the state. See [control names](/control_names.md "wikilink") for a list of valid names.
-   **state:** the new control state. *true* means pressed, *false* is released.

### Returns

Returns *true* if successful, *false* if otherwise.

Example
-------

<section name="Client" class="client" show="true">
``` lua
function newPed()
  local x, y, z = getElementPosition(localPlayer)
  local myPed = createPed(0, x + 1, y, z)
  if myPed then 
    setPedControlState(myPed,"forwards", true)
  end 
end
addCommandHandler("ped",newPed)
```

</section>
See Also
--------
