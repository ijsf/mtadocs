This function removes every weapons from a specified [ped](/docs/ped.md "wikilink"), rendering it unarmed.

Syntax
------

``` lua
bool takeAllWeapons ( ped thePed )
```

### Required Arguments

-   **thePed**: A [ped](/docs/ped.md "wikilink") element referencing the specified ped

### Returns

Returns *true* if the function succeeded, *false* otherwise.

Example
-------

This example removes all weapons from every player

``` lua
takeAllWeapons ( getRootElement() )  --remove all the weapons
outputChatBox ( "Weapons are not permitted!" ) --tell the players why they lost their weapons
```

See Also
--------

[ru:takeAllWeapons](/docs/ru:takeallweapons.md "wikilink")
