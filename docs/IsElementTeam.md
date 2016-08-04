<lowercasetitle/>

This function checks if element is team.

Syntax
------

``` lua
 bool isElementTeam( element theElement ) 
```

### Returns

Returns true if the element is team, otherwise false.

### Code

``` lua

function isElementTeam(theTeam)
   if isElement(theTeam) and (getElementType ( theTeam ) == "team") then
        return true
   end  
    return false
end
```

### Example

<section name="Client" class="client" show="true">
``` lua
```

</section>
Author: Booo

See Also
--------
