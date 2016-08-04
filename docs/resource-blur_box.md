This resource lets You create simple gaussian blur boxes onClientRender. Using that - You can make your game GUI a bit more fancy.

Overview
--------

It is easy to use, gives a few options to manage blur boxes.

The resource itself adds exported clientside functions:

Exported functions
------------------

#### createBlurBox

<section name="Client" class="client" show="true">
This function creates a blur box.

``` lua
bool exports.blur_box:createBlurBox(float posX,posY,sizeX,sizeY,int colorR,colorG,colorB,colorA,postGUI)
```

### Required Arguments

-   **float posX, posY:** Position in screen space.
-   **float sizeX, sizeY:** Size of the box.
-   **int colorR,colorG,colorB,colorA:** RGBA color (0 - 255).
-   **bool postGUI:** Should the box be drawn before or after MTA GUI elements.

### Returns

The function returns the element if set successfully, 'false' otherwise.

</section>
#### destroyBlurBox

<section name="Client" class="client" show="true">
This function destroys a blur box element.

``` lua
bool exports.blur_box:destroyBlurBox(element blurBoxElement)
```

### Required Arguments

-   **element blurBoxElement:** A previously declared blur box element.

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setBlurBoxEnabled

<section name="Client" class="client" show="true">
This function enables or disables a created blur box element.

``` lua
bool exports.blur_box:setBlurBoxEnabled(element blurBoxElement, bool isEnabled)
```

### Required Arguments

-   **element blurBoxElement:** A previously declared blur box element.
-   **bool isEnabled:** Enable/Disable the blur box element.

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setBlurBoxPosition

<section name="Client" class="client" show="true">
This function sets blur box position.

``` lua
bool exports.blur_box:setBlurBoxPosition(element blurBoxElement,float posX,posY)
```

### Required Arguments

-   **element blurBoxElement:** A previously declared blur box element.
-   **float posX, posY:** Position in screen space.

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setBlurBoxSize

<section name="Client" class="client" show="true">
This function sets blur box width and height.

``` lua
bool exports.blur_box:setBlurBoxSize(element blurBoxElement,float sizeX,sizeY)
```

### Required Arguments

-   **element blurBoxElement:** A previously declared blur box element.
-   **float sizeX,sizeY:** Size of the blur box.

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setBlurBoxColor

<section name="Client" class="client" show="true">
This function sets blur box color values.

``` lua
bool exports.blur_box:setBlurBoxColor(element blurBoxElement,float colorR,colorG,colorB,colorA)
```

### Required Arguments

-   **element blurBoxElement:** A previously declared blur box element.
-   **float colorR,colorG,colorB,colorA:** RGBA color (0 - 255).

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setBlurIntensity

<section name="Client" class="client" show="true">
This function sets blur amount for all the blur boxes

``` lua
bool exports.blur_box:setBlurIntensity(float blurFactor)
```

### Required Arguments

-   **float blurFactor:** Set blur amount for all the blur boxes. (default 0.6)

### Returns

The function returns true if set successfully, false otherwise.

</section>
#### setScreenResolutionMultiplier

<section name="Client" class="client" show="true">
This function sets screen relative resolution multiplier for the screenSource

``` lua
bool exports.blur_box:setScreenResolutionMultiplier(element blurBoxElement, float x,y)
```

### Required Arguments

-   **element blurBoxElement:** A previously declared blurBox element.
-   **float x,y:** Set sampled screen relative resolution multiplier (0-1)

### Returns

The function returns true if set successfully, false otherwise.

</section>
Examples
--------

``` lua
local scx, scy = guiGetScreenSize()
local guiWindowElement = nil
local blurBoxElement = nil

addEventHandler( "onClientPreRender", root,
    function()
        if guiWindowElement and blurBoxElement then
            local xPos, yPos = guiGetPosition ( guiWindowElement , false )
            local xSize, ySize = guiGetSize ( guiWindowElement , false )
            exports.blur_box:setBlurBoxPosition( blurBoxElement, xPos, yPos )
            exports.blur_box:setBlurBoxSize( blurBoxElement, xSize, ySize )     
        end
    end
,true ,"high-3" )   

addEventHandler( "onClientResourceStart", getResourceRootElement( getThisResource()),
function()
    guiWindowElement = guiCreateWindow ( scx/2-scy/4, scy/2 - scy/4, scy/2, scy/2, "BlurBox test", false )
    guiWindowSetMovable ( guiWindowElement, true )
    guiWindowSetSizable ( guiWindowElement, true )
    guiSetAlpha ( guiWindowElement, 0.3 )
    blurBoxElement = exports.blur_box:createBlurBox( scx/2-scy/4, scy/2 - scy/4, scy/2, scy/2, 255, 255, 255, 255, false )
    --exports.blur_box:setBlurBoxColor( blurBoxElement, 255, 100, 100, 255)
    exports.blur_box:setScreenResolutionMultiplier( 0.5, 0.5 )
end
)

addEventHandler( "onClientResourceStop", getResourceRootElement( getThisResource()),
function()
    destroyElement( guiWindowElement )
    blurBoxElement = not exports.blur_box:destroyBlurBox( blurBoxElement )
end
)
```

This creates a blur box and attaches it to a created window element.

Of course when you want to use these functions in your resources you have to include the blur\_box resource in meta.

[Blurbox example](/docs/file-15323.png.md "wikilink")

See Also
--------

[Community resource](http://community.multitheftauto.com/index.php?p=resources&s=details&id=10163)

[Test resource](https://www.dropbox.com/s/db13n4l62k21x19/blurBox_test.zip?dl=0)
