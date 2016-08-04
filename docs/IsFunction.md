This function will check all your functions, including other files of the same type ( client / server ), to see if it does exist. Please note that this will not check files from another type ( client / server ).

Syntax
------

``` lua
bool isFunction ( string functionName )
```

### Required Arguments

-   **functionName**: The concerning function to see if it exists, the name should be a **string**.

Code
----

<section name="Server- and/or clientside script" class="both" show="true">
``` lua
function isFunction ( functionName )
    if ( _G [ functionName ] == nil ) then
        _G [ functionName ] = loadstring ( functionName );
    end
    
    if ( _G [ functionName ] ~= nil ) then
        return true;
    end
    return false;
end
```

</section>
Example
-------

<section name="Server" class="server" show="true">
The following example adds a command to see if a function exists.

``` lua
addCommandHandler ( "isFunc",
    function ( thePlayer, _, functionName )
        outputChatBox ( tostring ( isFunction ( functionName  ) ), thePlayer );
    end
);
```

</section>
Author: Tosfera

See Also
--------
