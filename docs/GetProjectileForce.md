This function returns the force of the specified projectile.

Syntax
------

``` lua
float getProjectileForce ( projectile theProjectile )
```

### Required Arguments

-   **theProjectile:** The [projectile](/docs/projectiles.md "wikilink") element which force you want to retrieve.

Returns
-------

Returns a [float](/docs/float.md "wikilink") if successful, *false* otherwise.

Example
-------

**Example 1:** This example would outputs the force of the projectile on 1-100 scale. This function just works with projectiles which you throw so just grenades, satchel charge etc

``` lua

addEventHandler("onClientProjectileCreation", getRootElement(),
--The source of this event is the projectile that was created.
function ()
    local getForce = getProjectileForce(source)
    outputChatBox(getForce*100) -- outputs the force of the projectile on 1-100 scale
end
)
```

See also
--------

[it:getProjectileForce](/docs/it:getProjectileForce.md "wikilink")
