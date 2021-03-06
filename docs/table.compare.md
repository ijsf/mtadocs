<lowercasetitle></lowercasetitle>

This function check if both tables is equal.

Syntax
------

``` lua
boolean table.compare( table a, table a2 )
```

### Required Arguments

-   **a**: The table to check.
-   **a2**: The table to check.

### Note

This function equal only number and string values of tables. All other types ignored!
See examples.

### Returns

Returns true if tables is equal.

<section name="Code" class="both" show="true">
``` lua
function table.compare( a1, a2 )
    if 
        type( a1 ) == 'table' and
        type( a2 ) == 'table'
    then
    
        local function size( t )
            if type( t ) ~= 'table' then
                return false 
            end
            local n = 0
            for _ in pairs( t ) do
                n = n + 1
            end
            return n
        end

        if size( a1 ) == 0 and size( a2 ) == 0 then
            return true
        elseif size( a1 ) ~= size( a2 ) then
            return false
        end
        
        for _, v in pairs( a1 ) do
            local v2 = a2[ _ ]
            if type( v ) == type( v2 ) then
                if type( v ) == 'table' and type( v2 ) == 'table' then
                    if size( v ) ~= size( v2 ) then
                        return false
                    end
                    if size( v ) > 0 and size( v2 ) > 0 then
                        if not table.compare( v, v2 ) then 
                            return false 
                        end
                    end 
                elseif 
                    type( v ) == 'string' or type( v ) == 'number' and
                    type( v2 ) == 'string' or type( v2 ) == 'number'
                then
                    if v ~= v2 then
                        return false
                    end
                else
                    return false
                end
            else
                return false
            end
        end
        return true
    end
    return false
end
```

</section>
<section name="Example" class="both" show="true">
``` lua
--[[
 Well all noobs can say about this function is suck because i can compare both tables like this:
 a = { 1 }
 a2 = { 1 }
 print( a == a2 ) --> FALSE
 
 It's LIE!

 Here is compare userdata of both tables.
]]


local a1 = { 1, 2, 3 }
local a2 = { 1, 2, 3 }

print( table.compare( a1, a2 ) ) --> TRUE condition working. Because tables are same.

local a3 = { 1, { 2, 4 }, 5 }
local a4 = { 1, { 2, 4 }, 5 }

print( table.compare( a3, a4 ) ) --> TRUE condition working. Because tables are same.

local a5 = { { 1, 2, 3 }, 5 }
local a6 = { 1, 5 }

print( table.compare( a5, a6 ) ) --> FALSE condition doesn't working. Because tables are not same.


local a7 = { 'a', 'b' }
local a8 = { 'a', 'b' }

print( table.compare( a7, a8 ) ) --> TRUE condition working. Because tables are same.

local a9 = { 1, {}, 5 }
local a10 = { 1, {}, 5 }

print( table.compare( a9, a10 ) ) --> TRUE condition working. Because tables are same.
```

</section>
Author: Kenix

See Also
--------
