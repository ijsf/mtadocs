Please use [setElementModel](/docs/setelementmodel.md "wikilink")

This sets a new object model to the specified element.

Syntax
------

``` lua
bool setObjectModel ( object theObject, int id )        
```

### Required Arguments

-   **theObject:** A valid [object](/docs/object.md "wikilink").
-   **id:** An [int](/docs/int.md "wikilink") specifying the model id.

### Returns

Returns *true* if the model change was successful, *false* otherwise.

Example
-------

<section name="Server" class="server" show="true">
This will continually change an object model every 2.5 seconds at the location -1084.52, -1634.81, 76.36 (Truth's farm).

``` lua
myobject = createObject ( 5822, -1084.52, -1634.81, 76.36 )
-- We create an initial object element. I choose object model 5822 to begin with.

function objectRandomization ()  
    local randomobjectnumber = math.random(1, 18000)
    -- Choose a random number between 1 and 18000 as a whole integer and assign it to
    -- the variable 'randomobjectnumber'
    setObjectModel ( myobject, randomobjectnumber )
    -- Change our object appearance by applying a new model ID
end

setTimer ( objectRandomization, 2500, 0 )
-- Every 2.5 seconds, the function 'objectRandomization' is called by this timer.
-- Each time the function runs, it changes the object model by applying a new whole-
-- integer random object ID. This timer is called an infinite amount of times since  
-- its repeat value is set to 0.
```

</section>
See Also
--------
