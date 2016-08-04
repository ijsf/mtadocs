Sets the walking style of a ped. A walking style consists of a set of animations that are used for walking, running etc.

Syntax
------

``` lua
bool setPedWalkingStyle ( ped thePed, int style )
```

### Required Arguments

-   **thePed:** the ped whose walking style to change.
-   **style:** the walking style to set.

The possible walking styles are:

### Returns

Returns *true* if successful, *false* otherwise.

Example
-------

<section name="Client example" class="client" show="true">
Changes the walking style of the player to Drunkman when the resource is started

``` lua
function onClientResourceStart()
    setPedWalkingStyle(localPlayer,126) 
end
addEventHandler("onClientResourceStart",resourceRoot, onClientResourceStart)
```

</section>
See Also
--------
