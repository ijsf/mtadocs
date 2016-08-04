Syntax
------

``` lua
table getEventHandlers ( string eventName, element attachedTo )
```

### Required Arguments

-   **eventName:** The name of the event. For example ( “onPlayerWasted” ).
-   **attachedTo:** The [element](/docs/element.md "wikilink") attached to.

### Returns

Returns table with attached functions, false otherwise.

### Example

<section name="Server" class="server" show="true">
``` Lua
function isEventHandlerAdded( sEventName, pElementAttachedTo, func )
    if 
        type( sEventName ) == 'string' and 
        isElement( pElementAttachedTo ) and 
        type( func ) == 'function' 
    then
        local aAttachedFunctions = getEventHandlers( sEventName, pElementAttachedTo )
        if type( aAttachedFunctions ) == 'table' and #aAttachedFunctions > 0 then
            for i, v in ipairs( aAttachedFunctions ) do
                if v == func then
                    return true
                end
            end
        end
    end

    return false
end

function onPlayerWasted()
    outputChatBox( getPlayerName( source ) .. ' died.' )
end
addEventHandler( 'onPlayerWasted', root, onPlayerWasted )

addCommandHandler( 'removeOnPlayerWastedEvent',
    function()
        if isEventHandlerAdded( 'onPlayerWasted', root, onPlayerWasted ) then
            outputChatBox( 'onPlayerWasted succesfully removed!' )
            removeEventHandler( 'onPlayerWasted', root, onPlayerWasted )
        end
    end
)
```

</section>
See also
--------
