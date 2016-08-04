This function is used to retrieve the type of an element.

Syntax
------

``` lua
string getElementType ( element theElement )  
```

### Required Arguments

-   **theElement:** The [element](/docs/element.md "wikilink") you wish to get the type of.

### Returns

Returns a *string* containing the element type, *false* if invalid arguments were passed.

Example
-------

<section name="Server" class="server" show="true">
This example destroys a haystack when a player targets it

``` lua
function onPlayerTarget ( targetElem )
    -- if the targeted object is a haystack (an object with model ID 3374) remove it from the game
    if getElementType ( targetElem ) == "object" and getElementModel ( targetElem ) == 3374 then
        destroyElement ( targetElem )
    end
end
addEventHandler ( "onPlayerTarget", root, onPlayerTarget )    -- add above function as handler for targeting event
```

</section>
See Also
--------
