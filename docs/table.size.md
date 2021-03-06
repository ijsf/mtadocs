<lowercasetitle></lowercasetitle>

This function returns the total size of a table and not only the highest numerical index like table.maxn or the number of fields that have a numerical index like the \#-operator.

Syntax
------

``` lua
int table.size( table tab )
```

### Required Arguments

-   **tab**: The table to retrieve the total size of.

### Returns

Returns the total number of fields the table contains.

Code
----

<section name="Server- and/or clientside Script" class="both" show="true">
``` lua
function table.size(tab)
    local length = 0
    for _ in pairs(tab) do length = length + 1 end
    return length
end
```

</section>
Example
-------

<section name="Server- and/or clientside Script" class="both" show="true">
<code lang="lua"> local tab = { 1, 2, 3, \[25\] = 4, five = 5, foo = “bar” } outputChatBox(tostring(\#tab)) --prints: 4 (because there are 4 fields with a numerical index) outputChatBox(tostring(table.maxn(tab))) --prints: 25 (because the highest numerical index is 25) outputChatBox(tostring(table.size(tab))) --prints: 6 (because the table has 6 fields in total)

</syntaxhighlight>
</section>
Author: NeonBlack

See Also
--------
