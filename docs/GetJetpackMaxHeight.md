This function gets the maximum height at which your jetpack can fly without failing to go higher.

Syntax
------

``` lua
float getJetpackMaxHeight ( )
```

### Returns

Returns a float containing the max jetpack height.

Example
-------

<section name="Client" class="client" show="true">
This example returns the max jetpack height to a player if they use the command 'jetpackmaxheight'.

``` lua
function commandGetJetpackMaxHeight()
   local height = getJetpackMaxHeight() or "N/A"
   outputChatBox("Jetpack max height: "..height, 0, 255, 0)
end
addCommandHandler("jetpackmaxheight", commandGetJetpackMaxHeight)
```

</section>
See Also
--------
