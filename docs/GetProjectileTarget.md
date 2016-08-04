This function returns the target of the specified projectile.

Syntax
------

``` lua
element getProjectileTarget ( projectile theProjectile )
```

### Required Arguments

-   **theProjectile:** The [projectile](/docs/projectiles.md "wikilink") element which target you want to retrieve.

Returns
-------

Returns the [element](/docs/element.md "wikilink") which is the projectile's target if the projectile is valid and can have a target (like a heat-seeking rocket), *false* otherwise.

Example
-------

This example allows a player to send projectiles at other players.

``` lua
function projectileCreating(command,targetPlayer)
    local x,y,z = getElementPosition(getLocalPlayer()) -- Get the position of the player
    local target = getPlayerFromName(targetPlayer) or nil -- Get the target, or set it to nil if no target specified
    local theProjectile = createProjectile(thePlayer,20,x,y,z+50,1.0,target)
    if (target) then
        outputChatBox("Created projectile's target: "..getPlayerName(getProjectileTarget(theProjectile)))
    else
        outputChatBox("Created projectile with no target")
    end
end
addCommandHandler("rocket",projectileCreating) -- Bind the 'rocket' command to projectileCreating function
```

See also
--------

[it:getProjectileTarget](/docs/it:getProjectileTarget.md "wikilink")
