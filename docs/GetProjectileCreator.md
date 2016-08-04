This function returns the creator of the specified projectile.

Syntax
------

``` lua
element getProjectileCreator ( projectile theProjectile )
```

### Required Arguments

-   **theProjectile:** The [projectile](/projectiles.md "wikilink") element which creator you want to retrieve.

Returns
-------

Returns the element which created the projectile if successful, *false* otherwise.

Example
-------

<section name="Client" class="client" show="true">
This example will output a message in the chatbox saying who created the projectile.

``` lua
addEventHandler("onClientProjectileCreation", root, function(projectile)
    local creator = getProjectileCreator(projectile)
    if (getElementType(creator) == "player") then
        local pName = getPlayerName(creator)
    local projectileID = getProjectileType(projectile)
        outputChatBox(pName.." created a projectile! (ID: "..projectileID..")", 255, 200, 0, false)
    end
end)
```

</section>
See also
--------

[it:getProjectileCreator](/it:getProjectileCreator.md "wikilink")
