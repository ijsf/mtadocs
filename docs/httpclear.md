This function removes all text from the current HTML output.

Syntax
------

``` lua
bool httpClear ( )
```

### Returns

Returns *true* if the output buffer was cleared successfully, *false* otherwise.

Example
-------

This sample resource page adds a message to be outputted saying there are players in the server, but clears output if the server is empty so a blank page is displayed instead.

``` html
<html>
   <head/>
   <body>
      There are some players in the server.
   </body>
</html>
<*
```

``` lua
if getPlayerCount() == 0 then
   httpClear()
end
```

``` html
*>
```

See Also
--------
