This function gets the name of the specified resource.

Syntax
------

``` lua
string getResourceName ( resource res )
```

### Required Arguments

-   **res:** The resource you wish to get the name of.

### Returns

Returns a string with the resource name in it, or *false* if the resource does not exist.

Example
-------

<section class="server" name="Server" show="true">
This simple example outputs a message in the console whenever a resource starts, stating the name of the resource.

``` lua
addEventHandler("onResourceStart", getRootElement(),
    function(res)
        outputConsole("Resource " .. getResourceName(res) .. " just started.")
    end
)
```

</section>
See Also
--------
