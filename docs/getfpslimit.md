This function retrieves the maximum [FPS (Frames per second)](http://en.wikipedia.org/wiki/Frame_rate) that players on the server can run their game at.

Syntax
------

``` lua
int getFPSLimit ()         
```

### Returns

Returns an integer between **25** and **100** of the maximum FPS that players can run their game at.

Example
-------

This example displays a message in the chatbox showing the current fps limit.

``` lua
function fpsLim()
        outputChatBox ( "The FPS limit is: " .. getFPSLimit () )
end                                                  

-- Add console command "fpslimit" which calls the function fpsLim
addCommandHandler ( "fpslimit", fpsLim )
```

[pl:getFPSLimit](/docs/pl:getFPSLimit.md "wikilink")

See Also
--------
