Parameters
----------

*None*

Source
------

The [source](/event_system#Event_source.md "wikilink") of this event is the element that fired the weapon. If the server is the creator it returns *nil*.

Cancel effect
-------------

If this event is [canceled](/Event_system#Canceling.md "wikilink"), the bullet(s) won't be synced with other players.

Requirements
------------

Example
-------

``` lua
addEventHandler( "onWeaponFire", root,
    function ()
        if ( isElement( source ) ) and ( getElementType( source ) == "player" ) then
            outputChatBox( "You fired a weapon!", source, 0, 225, 0 )
        end
    end
)
```

[ru:OnWeaponFire](/ru:OnWeaponFire.md "wikilink")
