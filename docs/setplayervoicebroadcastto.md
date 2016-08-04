<div style="border: 1px dotted blue; background: #00CC66;padding:4px;margin-bottom:2px;">
**Note**: This function should only be used as a low-level function for advanced users. For typical Voice scripting, please see the [Voice Resource](/docs/resource:voice.md "wikilink")

</div>
This function allows you to change who can hear the voice of a player.

Syntax
------

``` lua
bool setPlayerVoiceBroadcastTo ( element thePlayer, mixed broadcastTo )
```

### Required Arguments

-   **thePlayer:** The [player](/docs/player.md "wikilink") you wish to change
-   **broadcastTo :** Element or table of elements who should hear the voice from this player

### Returns

Returns *true* if the value was set successfully, *false* otherwise.

Example
-------

<section name="Server" class="server" show="true">
    function getPlayer( ... )
        if ( ... ) then
            
            local elements = {};
            for _, string in ipairs( { ... } ) do
                for _, element in ipairs( getElementsByType( 'player' ) ) do
                    if ( string.find( string:lower(), getPlayerName(element):lower(), 1, true ) ) then
                        table.insert( elements, element );
                    end
                end
            end
            
            return elements;
        end
        
        return false
    end

    addCommandHandler( 'broadcast', 
        function( player, command, target, target_ )
            if ( target and target_ ) then
                target, target_ = getPlayer( target, target_ );
                if ( target and target_ ) then
                    setPlayerVoiceBroadcastTo( target, target_ );
                else
                    outputChatBox( not target and "Target 1 not found!" or not target_ and "Target 2 not found!", root, 255, 0, 0, false );
                end
            end
        end
    )

</section>
See Also
--------
