[thumb|200px|Blood splatter](/docs/Image:Fxblood.png.md "wikilink") Creates a blood splatter particle effect.

Syntax
------

``` lua
bool fxAddBlood ( float posX, float posY, float posZ, float dirX, float dirY, float dirZ, [int count=1, float brightness=1.0] )
```

### Required Arguments

-   **posX, posY, posZ:** the world coordinates where the effect originates.
-   **dirX, dirY, dirZ:** a direction vector indicating where the blood flies to.

### Optional Arguments

-   **count:** the number of flying droplets to create.
-   **brightness:** the brightness. Ranges from 0 (almost black) to 1 (normal color).

Example
-------

<section name="Client" class="client" show="true">
This example creates blood effects when a player gets shot.

``` lua
function BloodonDamage( attacker, weapon, bodypart, loss )
   if loss > 25 then -- if the player loses more than 25 hp, then...
      local x, y, z = getElementPosition( source ) -- get player's position for adding blood
      local randombloodamount = math.random( 1, 3 ) -- random blood amount 1-3
      fxAddBlood ( x, y, z-2, 0.00000, 0.00000, 0.00000, randombloodamount, 1 )
      -- this adds blood to player's current position
   end
end
addEventHandler( "onClientPlayerDamage", root, BloodonDamage ) -- calls the function when a player loses hp
```

</section>
See Also
--------

[ru:FxAddBlood](/docs/ru:FxAddBlood.md "wikilink")
