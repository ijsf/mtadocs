[Category:Incomplete](/Category:Incomplete.md "wikilink") The Vector2 class is a class introduced in 1.4

Methods
-------

### create

This is default constructor for the Vector2 class and returns a Vector2 object.

#### Syntax

``` lua
vector2 Vector2 ( float x = 0, float y = 0 )
```

-   **x**, and **y** coordinates for the vector. If not specified, they default to 0.
-   Instead of these two coordinates, a single Vector2 object may be inserted to clone it.

#### Example

This example checks if the player is using a low resolution.

<section name="Client" class="client" show="true">
``` lua
function resolution ()
   local screenSize = Vector2(guiGetScreenSize())
   if ( screenSize.x <  1360 ) and ( screenSize.y < 768 ) then 
     outputChatBox ("You are running on a low resolution")
   end
end
addEventHandler ( "onClientResourceStart",resourceRoot,resolution)
```

</section>
### normalize

### dot

### getX/Y and setX/Y

These functions allow you get and set specific coordinates:

-   getX and setX
-   getY and setY

#### Generic set syntax

``` lua
bool vec:setX ( float x = 0 )
```

-   **x**: number value to set the coordinate to
-   This value can also be set by the variable **vec.x**
-   Returns *true* if doesn't fail

#### Generic get syntax

``` lua
float vec:getX()
```

-   This value can also be accessed by the variable **vec.x**
-   Returns a **float** if doesn't fail

### getNormalized

### getSquaredLength

### getLength
