This function checks the given arguments and calls the error-function if something is wrong. Finally it makes debugging easier since you'll get useful error-messages when calling a selfmade function with wrong or malformed arguments.

Syntax
------

``` lua
 )
```

### Required Arguments

-   **funcname**: Name of the function in which the Check-function is called.
-   **types1**: Type(s) that arg1 should/may be of. It's a string if only one type is possible, otherwise it can be a table with strings. Possible types are “nil”, “boolean”, “number”, “string”, “function”, “table”, “thread” and “userdata”.
-   **arg1**: Value of the argument that should be checked.
-   **argname1**: Name of the argument whose value is arg1.

### Optional Arguments

-   **...**: You may pass as many triples as you want to.

Code
----

<section name="Server- and/or clientside Script" class="both" show="true">
``` lua
function Check(funcname, ...)
    local arg = {...}
    
    if (type(funcname) ~= "string") then
        error("Argument type mismatch at 'Check' ('funcname'). Expected 'string', got '"..type(funcname).."'.", 2)
    end
    if (#arg % 3 > 0) then
        error("Argument number mismatch at 'Check'. Expected #arg % 3 to be 0, but it is "..(#arg % 3)..".", 2)
    end
    
    for i=1, #arg-2, 3 do
        if (type(arg[i]) ~= "string" and type(arg[i]) ~= "table") then
            error("Argument type mismatch at 'Check' (arg #"..i.."). Expected 'string' or 'table', got '"..type(arg[i]).."'.", 2)
        elseif (type(arg[i+2]) ~= "string") then
            error("Argument type mismatch at 'Check' (arg #"..(i+2).."). Expected 'string', got '"..type(arg[i+2]).."'.", 2)
        end
        
        if (type(arg[i]) == "table") then
            local aType = type(arg[i+1])
            for _, pType in next, arg[i] do
                if (aType == pType) then
                    aType = nil
                    break
                end
            end
            if (aType) then
                error("Argument type mismatch at '"..funcname.."' ('"..arg[i+2].."'). Expected '"..table.concat(arg[i], "' or '").."', got '"..aType.."'.", 3)
            end
        elseif (type(arg[i+1]) ~= arg[i]) then
            error("Argument type mismatch at '"..funcname.."' ('"..arg[i+2].."'). Expected '"..arg[i].."', got '"..type(arg[i+1]).."'.", 3)
        end
    end
end
```

</section>
Example
-------

<section name="Server- and/or clientside Example" class="both" show="true">
This example shows the Check-function's usage in case of a more or less useless division function.

``` lua
-- define the function
function divide(dividend, divisor, round)
    -- check the passed arguments
    Check("divide", "number", dividend, "dividend", "number", divisor, "divisor", {"nil","boolean"}, round, "round")

    -- error if divisor is 0
    if (divisor == 0) then error("Someone tried to divide by 0. YOU MUST NOT DO THAT!!!") end

    -- calculate the result
    local quotient = dividend / divisor
    -- round the result if round is true
    if (round) then quotient = math.floor(quotient + .5)

    -- return the result
    return quotient
end
```

</section>
Author: NeonBlack

See Also
--------
