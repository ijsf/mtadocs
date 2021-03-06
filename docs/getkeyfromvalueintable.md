This function can be used to find the key of a specified value in a specified table.

Syntax
------

``` lua
element/int/float/string getKeyFromValueInTable(table theTable, mixed searchFor )
```

### Required Arguments

-   **theTable**: The table where to look for the specified value.
-   **searchFor**: The string/number/element to find the key of.

### Returns

Returns the key of the searched value, or *false* if not found.

Code
----

<section name="Function source" class="both" show="true">
``` lua
function getKeyFromValueInTable(a, b)
    for k,v in pairs(a) do
        if v == b then
           return k
        end
    end
    return false
end
```

</section>
Author: MrTasty

Example
-------

This example output the cost of the item specified by the player who entered the command.

**NOTE:** This is not the most efficient way, as it won't allow you to have more than 1 item of the same cost.

``` lua
shopItems = {
    --[PRICE] = "ITEM NAME",
    [10] = "Sprunk Soda",
    [12] = "eCola",
    [17] = "Pisswasser",
}

addCommandHandler("getcostof", function(player, command, item)
    if item then
        local cost = getKeyFromValueInTable(shopItems, item) --Find the key (the price in this case) of entered item name
        if cost then
            outputChatBox(item.." costs $"..cost, player, 255, 0, 0) --If the cost was found, output it to the command executor
        else
            outputChatBox(item.." is not available in our shop.", player, 255, 0, 0) --If it wasn't, tell the command executor that the item does not have a cost (ie: not in the shop)
        end
    else
        outputChatBox("Syntax error. Valid syntax is: /"..command.." <item name>", player, 255, 0, 0) --Output valid syntax in case the executor did not specify the item name to search for
    end
end)
```

See Also
--------
