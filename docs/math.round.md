<lowercasetitle></lowercasetitle>

This function is a full featured round function for Lua's math-library. Bear in mind that both the floor and the ceil method may not work properly clientside when you pass something greater than 0 as second argument. This is because of some weird clientside number bug. It's fixed for the round method.

Syntax
------

``` lua
 )
```

### Required Arguments

-   **number**: The number to round.

### Optional Arguments

-   **decimals**: The number of decimals to keep.
-   **method**: The round method that should be used. Valid values are “round” (which is default), “floor” and “ceil”.

### Returns

Returns the rounded number.

Code
----

<section name="Server- and/or clientside Script" class="both" show="true">
<code lang="lua"> function math.round(number, decimals, method)

`   decimals = decimals or 0`
`   local factor = 10 ^ decimals`
`   if (method == `“`ceil`”` or method == `“`floor`”`) then return math[method](number * factor) / factor`
`   else return tonumber(("%."..decimals..`“`f`”`):format(number)) end`

end

</syntaxhighlight>
</section>
Example
-------

<section name="Serverside Example" class="server" show="true">
This example adds a command that outputs the players current position approximated to three decimals. <code lang="lua"> function pos(thePlayer, command)

`   local x, y, z = getElementPosition(getPedOccupiedVehicle(thePlayer) or thePlayer)`
`   outputChatBox(`“`Your` `current` `position:` `[`”`..math.round(x, 3).."|"..math.round(y, 3).."|"..math.round(z, 3).."]", thePlayer)`

end addCommandHandler(“pos”,pos)

</syntaxhighlight>
</section>
Author: NeonBlack

See Also
--------
