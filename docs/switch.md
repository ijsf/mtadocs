This function allow the value of a variable or expression to control the flow of program execution via a multiway branch.

Syntax
------

``` lua
var switch( arg )
```

### Required Arguments

-   **arg**: The expression to compare.

### Returns

Returns false if failed.

Code
----

<section name="Server- and/or clientside Script" class="both" show="true">
``` lua
function switch(arg)
        if(type(arg)~="table")then return switch end
        local switching, default, done; --Default is nil
        if(tostring(arg[1]):len()<=2)and(tostring(arg[2]):len()<=2)then switching=arg[1] end
        table.remove(arg, 1);
        for i=1, #arg do
                if(tostring(arg[i]):len()<=3)and(arg[i]==switching)then
                        if(type(arg[i+1])=="function")then
                                pcall(arg[i+1])
                                done=true;
                                break
                        else
                                break
                        end
                end
                if(arg[i]==nil)and(arg[i]==switching)and(type(arg[i+1])=="function")then pcall(arg[i+1]) end
        end
        if(not done)then print("No action.") end
end
```

</section>
Example
-------

<section name="Server" class="server" show="true">
This example compares a variable value and print out the result.

``` lua
Player = 0 -- The variable to compare
switch -- Using the function
{ -- Using curly braces as it's a table
Player; -- Put the expression to compare in here and don't forget to end it with a semi-colon
    0, function() print("It's 0") end, -- [ compare the value, do the function ] The first argument compares the value and the second execute the command inside the function if that compare is true.
    1, function() print("It's 1") end,
}
```

</section>
Author: TopAz

See Also
--------
