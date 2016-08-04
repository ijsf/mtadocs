This function returns the type of the specified projectile.

Syntax
------

``` lua
int getProjectileType ( projectile theProjectile )
```

### Required Arguments

-   **theProjectile:** The [projectile](/docs/Element/Projectile.md "wikilink") element which type you want to retrieve.

Returns
-------

Returns an [integer](/docs/int.md "wikilink") over the type of the projectile or *false* if invalid arguments were passed.

Example
-------

``` lua
function projectileCreation()
    local theType = getProjectileType(source)
    outputChatBox("A projectile was created! It's type: "..theType)
end
addEventHandler("onClientProjectileCreation", getRootElement(), projectileCreation)
```

See also
--------

[it:getProjectileType](/docs/it:getProjectileType.md "wikilink")
