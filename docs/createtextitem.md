<pageclass class="#228B22" subcaption="Useful Function"></pageclass> <lowercasetitle/>

**With this function you can create any text you want with any size color visible to who you want and this function server side only!**

Syntax
------

``` lua
bool CreateTextItem (  player playerToAdd , time, int red = 255, int green = 255, int blue = 255, float scale = 1, string text, [ float x, float y, string alignX = "left", string alignY = "top"] )
```

### Required Arguments

-   **playerToAdd: The player that should observe the textdisplay.**
-   **time: The number of times you want to the remove The textdisplay ,number of milliseconds (the minimum is 50)(1000 milliseconds = 1 second)**
-   **red: A value between 0 and 255 indicating how red the text should be.**
-   **green: A value between 0 and 255 indicating how green the text should be.**
-   **blue: A value between 0 and 255 indicating how blue the text should be.**
-   **scale: A floating point value indicating the scale of the text. The default is 1.0, which is around 12pt.**
-   **text: A string of text you want to display**

### Optional Arguments

-   x: A floating point number between 0.0 and 1.0 indicating how far across the screen the text should be shown, as a percentage of the width, from the left hand side.
-   y: A floating point number between 0.0 and 1.0 indicating how far down the screen the text should be shown, as a percentage of the height, from the top.
-   scale: A floating point value indicating the scale of the text. The default is 1.0, which is around 12pt.
-   alignX: A string representing the X-alignment of the text. (“left”, “center”, “right”)
-   alignY: A string representing the Y-alignment of the text. (“top”, “center”, “bottom”)

### Important Note

-   *'You can't use **'getRootElement()**' element you will get some errors you have to use getElementsByType to get All Players!*'

Code
----

<section name="Function source" class="server" show="true">
``` lua
function CreateTextItem ( player, time, r, g, b, scale, text, x, y, alignX, alignY)
    if not player or not time or not text then return end
    if not tonumber(r) and not tonumber(g) and not tonumber(b) then r, g, b = 255, 0, 0 end
    if not scale then scale = 1 end
    if ( isElement( player ) and type ( text ) == 'string' and tonumber( time) ) then
        local Display = textCreateDisplay ()
        local newtextItem = textCreateTextItem ( text, x or 0.5, y or 0.5, 2, r, g, b, 255, scale, alignX or "center", alignY or "center" )
        textDisplayAddText ( Display, newtextItem )
        textDisplayAddObserver ( Display, player )
        setTimer(textDestroyTextItem, time, 1, newtextItem)
        setTimer(textDestroyDisplay, time, 1, Display)
    end 
end
```

</section>
Example
-------

<section name="Server Example" class="server" show="true">
This Example creates a text item. A text item represents a single area of text, much like a label !

``` lua
addCommandHandler("Create",
function ( element , cmd , item ) 
    local Text = tostring ( item )
    if ( Text ) then
        CreateTextItem ( element, 5000, 255, 255, 0, 5,Text )
    end
end
)
```

</section>
Example
-------

<section name="Server Full Example" class="server" show="true">
This Example creates a text item. A text item represents a single area of text, much like a label !

``` lua
function CreateTextItem ( player, time, r, g, b, scale, text, x, y, alignX, alignY)
    if not player or not time or not text then return end
    if not r and not g and not b then r, g, b = 255, 0, 0 end
    if not scale then scale = 1 end
    if ( isElement( player ) and type ( text ) == 'string' and tonumber( time) ) then
        local Display = textCreateDisplay ()
        local newtextItem = textCreateTextItem ( text, x or 0.5, y or 0.5, 2, r, g, b, 255, scale, alignX or "center", alignY or "center" )
        textDisplayAddText ( Display, newtextItem )
        textDisplayAddObserver ( Display, player )
        setTimer(textDestroyTextItem, time, 1, newtextItem)
        setTimer(textDestroyDisplay, time, 1, Display)
    end 
end

addCommandHandler("Test",
function (  ) 
        for _,v in ipairs ( getElementsByType("player") ) do
        CreateTextItem ( v, 5000, 255, 255, 0, 5,"Test Text" )
    end
end
)
```

</section>
See Also
--------

[Category:Useful Functions](/docs/category:useful_functions.md "wikilink")
