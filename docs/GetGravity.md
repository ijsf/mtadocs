This function returns the current gravity level for the context in which it is called (server or client).

Syntax
------

``` lua
float getGravity()
```

### Returns

Returns a float with the current server or client (depending on where you call the function) gravity level.

Example
-------

<section name="Server" class="server" show="true">
This serverside command outputs the serverside gravity level.

``` lua
function getGravityLevel( playerSource )
    local gravity = getGravity ( )
    outputConsole ( "The gravity is currently set to " .. gravity, playerSource )
end
-- attach the 'getGravityLevel' function to the "gravity" command
addCommandHandler ( "gravity", getGravityLevel )
```

</section>
See Also
--------

[ru:getGravity](/docs/ru:getGravity.md "wikilink")
