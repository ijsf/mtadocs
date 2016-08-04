Get the time left before a projectile detonates.

Syntax
------

``` lua
int getProjectileCounter ( projectile projectile )
```

### Required Arguments

-   projectile: the projectile to get the timer of.

### Returns

Returns the the time in milliseconds to detonation which depending on the projectile type will do different things:

-   Grenades will explode when it hits 0
-   Teargas may be a duration timer
-   Both types of rockets will explode when it hits 0
-   Satchels restarts so I do not think it does anything

### Example

<section name="Client" class="client" show="true">
With this example you can find out how long does it take for a projectile to explode/end

``` lua
function getProjectileBoomTime()
outputChatBox("Time for "..getProjectileType(source).." to explode/end is "..getProjectileCounter(source).." miliseconds.",255,0,0)
end
addEventHandler("onClientProjectileCreation",root,getProjectileBoomTime)
```

</section>
Requirements
------------

See Also
--------
