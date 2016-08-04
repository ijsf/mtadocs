This function allows you to get elements in dimension.

**Important Note:** Remember that the element type which you type must be a **string**!.

Syntax
------

``` lua
table getElementsInDimension( string theType, int dimension )
```

### Required Arguments

-   **theType**: The element type which you want to get.
-   **dimension**: The dimension from which you wanna get your elements.

Source
------

``` lua
function getElementsInDimension(theType,dimension)
    local elementsInDimension = { }
      for key, value in ipairs(getElementsByType(theType)) do
        if getElementDimension(value)==dimension then
        table.insert(elementsInDimension,value)
        end
      end
      return elementsInDimension
end
```

Example
-------

This example is outputting on chatbox “You are in correct dimension!” for players in dimension 2.

    function getPlayers()
        local players = getElementsInDimension("player",2) -- Getting the players in dimension 2.
          for key, value in ipairs(players) do
          outputChatBox("You are in correct dimension!",value) -- Outputting our's message.
          end
    end

Author: xScatta

See Also
--------
