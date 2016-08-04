This function allows you to retrieve the interior of any element. An interior is the current loaded place, 0 being outside.

Syntax
------

``` lua
int getElementInterior ( element theElement )
```

### Required Arguments

-   **theElement:** The element of which you'd like to retrieve the interior

### Returns

Returns an [int](/docs/int.md "wikilink") for the interior if **theElement** is valid, *false* otherwise.

Example
-------

<section show="true" name="Server" class="server">
This example shows a player if he is outside or not, when he enters the command 'AmIOutside'.

``` lua
function AmIOutside ( thePlayer, command )
    if ( getElementInterior(thePlayer) == 0 ) then
        outputChatBox ( "Yes you are outside " .. getPlayerName(thePlayer), thePlayer )
    else
        outputChatBox ( "No you aren't outside " .. getPlayerName(thePlayer), thePlayer )
    end
end
addCommandHandler ( "AmIOutside", AmIOutside )
```

</section>
See Also
--------

[de:getElementInterior](/docs/de-getelementinterior.md "wikilink") [ar:getElementInterior](/docs/ar-getelementinterior.md "wikilink")
