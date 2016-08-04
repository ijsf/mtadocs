Syntax
------

``` lua
uint bitNot ( uint var )
```

### Required arguments

-   **var:** The value you want to perform a bitwise NOT on

### Returns

Returns the value on which the operation has been performed.

Example
-------

<section name="server" class="server" show="true">
--In this example we make a command which you can do a bitNot operator

``` lua
function bitnot(thePlayer,cmd,value)

    outputChatBox(bitNot(value),thePlayer)

end

addCommandHandler("bitnot",bitnotFunc)
```

</section>
See Also
--------
