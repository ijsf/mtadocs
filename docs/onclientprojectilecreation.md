This event is triggered when a [projectile](/docs/projectile.md "wikilink") is created.

Parameters
----------

``` lua
element creator
```

Source
------

The [source](/docs/event_system#event_source.md "wikilink") of this event is the [projectile](/projectile.md "wikilink") that was created.

Cancel effect
-------------

This event cannot be cancelled. To remove the projectile you can use setElementPosition (some where far away) and then destroyElement (which makes it explode).

Example
-------

This will output a chatbox message when someone creates a projectile.

``` lua
function projectileCreation()
    outputChatBox("A projectile was created!")
end
addEventHandler("onClientProjectileCreation", getRootElement(), projectileCreation)
```

This will punish a player for throwing a teargas grenade. When he throws it he keeps getting warped to the location where the teargas got created, and also the teargas keeps getting warped to it. This will result in +/-60hp loss for the creator.

``` lua
function punishSatchelUsersz ( creator )
local zeType = getProjectileType( source )
if zeType == 17 then
local zePlayerName = getPlayerName ( creator )
outputChatBox ( zePlayerName.." is a noob teargas user! But he got punished for it don't worry." )
local x, y, z = getElementPosition ( source ) --Getting the position from the projectile creator
setTimer ( setElementPosition, 50, 250, source, x, y, z-0.5 )
setTimer ( setElementPosition, 50, 250, creator, x, y, z-0.5 )
end
end
addEventHandler( "onClientProjectileCreation", getRootElement(), punishSatchelUsersz )
```

This will disable people from creating flares. ( Dropped by Hydras )

``` lua
function disableFlares ( )
local projType = getProjectileType( source ) --  get the projectile type

    if projType == 58 then -- if the projectile is a flare
    
    destroyElement(source) -- notice cancelEvent() does not work, so this destroys the projectile element after it was created.
        
    end

end 

addEventHandler( "onClientProjectileCreation", getRootElement(), disableFlares ) -- when a projectile gets created call disableFlares.
```

See Also
--------

### Client projectile events
