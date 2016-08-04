This function returns the current oxygen level of the specified [ped](/ped.md "wikilink").

Syntax
------

``` lua
float getPedOxygenLevel ( ped thePed )
```

### Required Arguments

-   **thePed:** The [ped](/ped.md "wikilink") whose oxygen level you want to check

### Returns

A *float* with the oxygen level, *false* if an invalid ped was given.

Example
-------

<section name="Client" class="client" show="true">
This example defines a “showoxygen” console command that shows the player that executes it which oxygen level he has.

``` lua
function showOxygen ( command )
    local oxygen = getPedOxygenLevel ( localPlayer )
    outputChatBox( "Your oxygen level: " .. oxygen )
end
addCommandHandler ( "showoxygen", showOxygen )
```

</section>
See Also
--------
