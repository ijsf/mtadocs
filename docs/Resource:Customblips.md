The **customblips** resource allows you to create Blip icons clientside that appear on radar and on the F11 map. Custom blips can be any image or GUI element.

Exported Client functions
-------------------------

-   **createCustomBlip**
    -   This function creates a custom blip using DirectX image functions. If the stream radius is lower than 180, then the blip will only appear when it is visible on the radar.

``` lua
customblip exports.customblips:createCustomBlip ( float worldX, float worldY, int imageWidth, int imageHeight, string imagePath, [float streamRadius = 500] )
```

-   **guiConvertToCustomBlip**
    -   This function creates a custom blip using any GUI element. If the stream radius is lower than 180, then the blip will only appear when it is visible on the radar.

``` lua
gui-elem exports.customblips:guiConvertToCustomBlip ( gui-element blipGUI, float worldX, float worldY, [float streamRadius = 500] )
```

-   **getCustomBlipStreamRadius**
    -   This function gets the current stream radius of a customblip. Note, stream radius does not affect the F11 map.

``` lua
float exports.customblips:getCustomBlipStreamRadius ( customblip theBlip )
```

-   **setCustomBlipStreamRadius**
    -   This function sets the current stream radius of a customblip. Note, stream radius does not affect the F11 map.

``` lua
bool exports.customblips:setCustomBlipStreamRadius ( customblip theBlip, float streamRadius )
```

-   **getCustomBlipPosition**
    -   This function gets the world position of a customblip.

``` lua
float worldX, float worldY exports.customblips:getCustomBlipPosition ( customblip theBlip )
```

-   **setCustomBlipPosition**
    -   This function sets the world position of a customblip.

``` lua
bool exports.customblips:setCustomBlipPosition ( customblip theBlip, float worldX, float worldY )
```

-   **setCustomBlipRadarScale**
    -   This function sets the scale (where 0 is invisible, and 1 is 100% size. Going beyond 1 will increase the size) of the blip when it appears on the radar, relative to the size specified during creation. Passing nil will default to GTA's radar blip size.

``` lua
bool exports.customblips:setCustomBlipRadarScale ( customblip theBlip, float scale )
```

-   **setCustomBlipAlpha**
    -   This function sets the alpha (values 0-1) of the blip, allowing the adjustment of transparency.

``` lua
bool exports.customblips:setCustomBlipAlpha ( customblip theBlip, float alpha )
```

-   **setCustomBlipVisible**
    -   This function sets the visibility of the blip. Invisible blips will not be drawn.

``` lua
bool exports.customblips:setCustomBlipAlpha ( customblip theBlip, bool visible )
```

-   **destroyCustomBlip**
    -   This function destroys a custom blip.

``` lua
bool exports.customblips:destroyCustomBlip ( customblip theBlip )
```

Examples
--------

**Example 1** This example creates a blip that says 'Spawn' at Toreno's house, using GUI

``` lua
addEventHandler ( "onClientResourceStart", getResourceRootElement(getThisResource()),
    function()
        local blip = guiCreateButton ( 0, 0, 25, 20, "Spawn", false )
        guiSetFont(blip,"default-small")
        exports.customblips:guiConvertToCustomBlip ( blip, -700, 960, 10 )
    end
)
```

**Example 2** This example creates an image blip of “icon.png” at 0,0 - assuming the size of the image is 20x20px.

``` lua
addEventHandler ( "onClientResourceStart", getResourceRootElement(getThisResource()),
    function()
        exports.customblips:createCustomBlip ( 0,0, 20, 20, "icon.png" )
    end
)
```

[ru:<Resource:Customblips>](/ru:Resource:Customblips.md "wikilink")
