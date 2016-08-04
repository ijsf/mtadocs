This function checks if the specified [ped](/ped.md "wikilink") is on fire or not.

Syntax
------

``` lua
bool isPedOnFire ( ped thePed )
```

### Required Arguments

-   **thePed**: The [ped](/ped.md "wikilink") to check.

### Returns

Returns *true* if the ped is on fire, *false* otherwise.

Example
-------

<section class="server" name="Server" show="true">
This example checks if a random player is on fire, and if so gives him a fire extinguisher.

``` lua
local randomPlayer = getRandomPlayer()
if isPedOnFire ( randomPlayer ) then
    giveWeapon ( randomPlayer, 42, 100, true )
end
```

</section>
See Also
--------
