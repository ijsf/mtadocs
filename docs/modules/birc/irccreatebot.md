This function is used to create an which are the basis of the module. is automatically executed for created bot for the current resource after bot creation.

Syntax
------

``` lua
ircbot ircCreateBot ( string botName )
```

### Required Arguments

-   **botName:** The name that ircbot will receive.

  
**Note:** Validity of the bot names are not checked. Make sure you enter a name the server you are connecting to accepts.

### Returns

Returns the pointer if passed arguments were valid, *false* otherwise.

Example
-------

This example creates an ircbot called *DummyBot* and stores it to variable theBot on resource start.

``` lua
function resourceStart()
    theBot = ircCreateBot ( "DummyBot" )
end
addEventHandler ( "onResourceStart", getResourceRootElement (), resourceStart )
```

See Also
--------
