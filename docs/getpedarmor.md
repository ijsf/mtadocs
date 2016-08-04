This function returns the current armor of the specified [ped](/docs/ped.md "wikilink").

Syntax
------

``` lua
float getPedArmor ( ped thePed )
```

### Required Arguments

-   **thePed:** The [ped](/docs/ped.md "wikilink") whose armor you want to check

### Returns

A *float* with the armor, *false* if an invalid ped was given.

Example
-------

<section name="Client" class="client" show="true">
This example defines a “showarmor” console command that shows the player that executes it how much armor he has.

``` lua
function showArmor ( )
    local me = getLocalPlayer ( )
    local armor = getPedArmor ( me )
    outputChatBox( "Your armor: " .. armor )
end
addCommandHandler ( "showarmor", showArmor )
```

</section>
See Also
--------
