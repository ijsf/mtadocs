This function checks whether health target markers are drawn as set by [setPedTargetingMarkerEnabled](/docs/setPedTargetingMarkerEnabled.md "wikilink") or not.

Syntax
------

``` lua
bool isPedTargetingMarkerEnabled ( )
```

### Returns

Returns *true* if the health target markers are enabled, *false* if not.

Example
-------

<section name="Client" class="client" show="true">
This example will toggle the targeting markers with the command /togtargetmarkers.

``` lua
function toggleTargetMarkers(cmd)
    local targets = isPedTargetingMarkerEnabled()
    setPedTargetingMarkerEnabled(not targets)
    outputChatBox("You have " .. (targets and "enabled" or "disabled") .. " target markers.", 0, 255, 0, false)
end
addCommandHandler("togtargetmarkers", toggleTargetMarkers)
```

</section>
See Also
--------
