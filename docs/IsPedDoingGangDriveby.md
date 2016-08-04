This function checks if the ped is in the driveby state.

Syntax
------

``` lua
bool isPedDoingGangDriveby ( ped thePed )
```

### Required Arguments

-   **thePed:** The [ped](/ped.md "wikilink") element whose state is to be checked.

### Returns

Returns **true** if the driveby state is enabled, **false** otherwise.

Example
-------

<section name="Client" class="client" show="true">
This example turns on driveby mode when the local player types *driveby* in the console.

``` lua
function setDoingDriveby ( )
        -- we check if local player isn't currently doing a gang driveby
        if not isPedDoingGangDriveby ( localPlayer ) then
                -- if he got driveby mode off, turn it on
                setPedWeaponSlot ( localPlayer, 4 )
                setPedDoingGangDriveby ( localPlayer, true )
        else
                -- otherwise, turn it off
                setPedWeaponSlot ( localPlayer, 0 )
                setPedDoingGangDriveby ( localPlayer, false )
        end
end
addCommandHandler ( "driveby", setDoingDriveby )
```

</section>
See Also
--------
