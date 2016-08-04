This function enables or disables glitches that are found in the original Single Player game that can be used to gain an advantage in multiplayer.

Users of the **fastmove** glitch may additionally want to install [this resource to disable crouchsliding](https://community.mtasa.com/index.php?p=resources&s=details&id=13368).

Syntax
------

``` lua
bool setGlitchEnabled ( string glitchName, bool enable )
```

### Required Arguments

-   **glitchName:** the name of the property to set. Possible values are:

-   **enable:** whether or not to enable the glitch.

### Returns

Returns *true* if successful, *false* otherwise.

Example
-------

This example enables all glitches in the server once the resource is loaded.

``` lua
local glitches = {"quickreload","fastmove","fastfire","crouchbug","highcloserangedamage","hitanim","fastsprint","baddrivebyhitbox","quickstand"}

function enableGlitches ()
   for _,glitch in ipairs(glitches) do
      setGlitchEnabled (glitch, true )
   end 
end
addEventHandler ( "onResourceStart", getResourceRootElement ( ),enableGlitches)
```

See Also
--------
