This function sets the driveby state of a ped.

Syntax
------

``` lua
bool setPedDoingGangDriveby ( ped thePed, bool state )
```

### Required Arguments

-   **thePed:** The [ped](/docs/ped.md "wikilink") element whose state is to be changed.
-   **state:** A [boolean](/docs/boolean.md "wikilink") value representing the drive-by state, *true* meaning enabled and *false* disabled.

### Returns

Returns *true* if the driveby state could be changed, *false* otherwise.

Example
-------

<section name="Client" class="client" show="true">
This example turns on driveby mode when the local player types *driveby* in the console.

``` lua
function setDoingDriveby ( )
        -- we check if local player isn't currently doing a gang driveby
        if not isPedDoingGangDriveby ( getLocalPlayer () ) then
                -- if he got driveby mode off, turn it on
                setPedWeaponSlot ( getLocalPlayer (), 4 )
                setPedDoingGangDriveby ( getLocalPlayer (), true )
        else
                -- otherwise, turn it off
                setPedWeaponSlot ( getLocalPlayer (), 0 )
                setPedDoingGangDriveby ( getLocalPlayer (), false )
        end
end
addCommandHandler ( "driveby", setDoingDriveby )
```

</section>
See Also
--------

[ru:setPedDoingGangDriveby](/docs/ru:setpeddoinggangdriveby.md "wikilink")
