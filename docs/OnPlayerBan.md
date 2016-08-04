This event is triggered when a player added a [ban](/ban.md "wikilink") (like [onBan](/onBan.md "wikilink")).

Parameters
----------

``` lua
ban banPointer, player responsibleElement
```

-   **banPointer**: The ban pointer which was added.
-   **responsibleElement**: The player who added the ban

Source
------

The [source](/event_system#Event_source.md "wikilink") of this event is the [player](/player.md "wikilink") who was banned.

Example
-------

This example outputs the responsible element and the banned player's name when a ban takes place.

``` lua
function outputBan ( banPointer, responsibleElement ) -- Define the banner and the ban pointer in the function.
    local banner = getPlayerName( responsibleElement ) or "Console" -- Get the banner's name.
    
    outputChatBox ( banner .." has banned ".. getPlayerName( source ) ..".", getRootElement(), 255, 0, 0 ) -- Output the ban.
end
addEventHandler ( "onPlayerBan", getRootElement(), outputBan ) -- Trigger the function when there is a ban.
```

Changelog
---------
