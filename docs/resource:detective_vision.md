This resource able players to see other ped/players below walls and check theys info. You can download it [here](http://community.multitheftauto.com/index.php?p=resources&s=details&id=2074).
[thumb|How its looks](/docs/Image:Dvision.png.md "wikilink")

Exported Functions
------------------

### addWindowInfo

<section name="Client" class="client" show="true">
By this function you can add custom values in info window.

Syntax
------

``` lua
bool [string] addWindowInfo ( { string valueName, string elementData, string/nil element, [ { table childValue1, table childValue2, ...} ] } )
```

Required Arguments
------------------

-   **valueName**: Name of value what will shows in window
-   **elementData**: Name of element data from what it will get values
-   **element**: Type of element for what will shows this value, can be “player”, “ped” or nil for both

Returns
-------

Returns true or false and error message if otherwise.

</section>
### removeWindowInfo

<section name="Client" class="client" show="true">
By this function you can add remove values from info window.

Syntax
------

``` lua
bool [string] removeWindowInfo ( string valueName [, string elementData, string element ] )
```

Required Arguments
------------------

-   **valueName**: Name of value what shows in window

Optimal Arguments
-----------------

-   **elementData**: Name of element data from what it get values
-   **element**: Type of element for what shows this value, can be “player” or “ped”

Returns
-------

Returns true or false if otherwise.

</section>
See also
--------

[MTA Forum topic](http://forum.mtasa.com/viewtopic.php?f=108&t=32886&p=345513#p345513)
