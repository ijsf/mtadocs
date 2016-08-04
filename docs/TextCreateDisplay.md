A [text display](/docs/textdisplay.md "wikilink") is like a canvas that can contain many [items of text](/textitem.md "wikilink"). Each display can be seen by multiple observers (players) and each player can see multiple displays.

Syntax
------

``` lua
textdisplay textCreateDisplay()
```

Required Arguments
------------------

*This function has no arguments.*

Example
-------

``` lua
function showTextDisplay ( player, command )
   local serverDisplay = textCreateDisplay()                             -- create a text display
   textDisplayAddObserver ( serverDisplay, player )                      -- make it visible to a player
   local serverText = textCreateTextItem ( "Hello world!", 0.5, 0.5 )    -- create a text item for the display
   textDisplayAddText ( serverDisplay, serverText )                      -- add it to the display so it is displayed
end
addCommandHandler( "showText", showTextDisplay )
```

See Also
--------
