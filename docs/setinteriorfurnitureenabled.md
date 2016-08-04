Syntax
------

``` lua
bool setInteriorFurnitureEnabled ( int roomID, bool enabled )          
```

### Required Arguments

-   **roomID:** The room type which you want disable or enable the furniture in:
    -   **0**: shop
    -   **1**: office
    -   **2**: lounge
    -   **3**: bedroom
    -   **4**: kitchen
-   **enabled**: A bool representing whether the interior furniture is enabled or disabled.

### Returns

Returns *true* if successful, *false* otherwise.

Example
-------

<section name="Client" class="client" show="true">
``` lua
-- Disable furnishing for all rooms
for i = 0, 4 do
    setInteriorFurnitureEnabled(i, false)
end
```

</section>
See Also
--------
