<lowercasetitle/>

This useful client function draws an image on any element you choose.

Syntax
------

``` Lua
 ) 
```

[thumb|Example of how it should looks like.|284x230px](/docs/File:DxDrawImageOnElement.png.md "wikilink")

Required arguments
------------------

-   *TheElement*: The element you want to draw the image on it.
-   *Image*: The image you want. Use [dxCreateTexture](/docs/dxCreateTexture.md "wikilink") to create it.

Optional arguments
------------------

-   *height*: The height of the text, it's 1 by default.
-   *distance*: The distance you will be able to view the image from, it's 20 by default.
-   *height*: The height of the image, it's 1 by default.
-   *width*: The width of the image, it's 1 by default.
-   *R*: The Red color code (0-255), it's 255 by default.
-   *G*: The Green color code (0-255), it's 255 by default.
-   *B*: The Blue color code (0-255), it's 255 by default.
-   *alpha*: The alpha of the image, it's 255 by default.

<!-- -->

-   **checkBuildings:** Allow the line of sight to be blocked by GTA's internally placed buildings, i.e. the world map.
-   **checkVehicles:** Allow the line of sight to be blocked by [vehicles](/docs/Vehicle.md "wikilink").
-   **checkPeds:** Allow the line of sight to be blocked by peds, i.e. [players](/docs/Player.md "wikilink").
-   **checkObjects:** Allow the line of sight to be blocked by [objects](/docs/Object.md "wikilink").
-   **checkDummies:** Allow the line of sight to be blocked by GTA's internal dummies. These are not used in the current MTA version so this argument can be set to *false*.
-   **seeThroughStuff:** Allow the line of sight to be blocked by translucent game objects, e.g. glass.
-   **ignoreSomeObjectsForCamera:** Allow the line of sight to be blocked by certain objects.
-   **ignoredElement:** Allow the line of sight to pass through a certain specified element.

Returns
-------

Returns *true* if successful, *false* otherwise.

Function source
---------------

<section name="Client" class="client" show="true">
    function dxDrawImageOnElement(TheElement,Image,distance,height,width,R,G,B,alpha)
                    local x, y, z = getElementPosition(TheElement)
                    local x2, y2, z2 = getElementPosition(localPlayer)
                    local distance = distance or 20
                    local height = height or 1
                    local width = width or 1
                                    local checkBuildings = checkBuildings or true
                                    local checkVehicles = checkVehicles or false
                                    local checkPeds = checkPeds or false
                                    local checkObjects = checkObjects or true
                                    local checkDummies = checkDummies or true
                                    local seeThroughStuff = seeThroughStuff or false
                                    local ignoreSomeObjectsForCamera = ignoreSomeObjectsForCamera or false
                                    local ignoredElement = ignoredElement or nil
                    if (isLineOfSightClear(x, y, z, x2, y2, z2, checkBuildings, checkVehicles, checkPeds , checkObjects,checkDummies,seeThroughStuff,ignoreSomeObjectsForCamera,ignoredElement)) then
                        local sx, sy = getScreenFromWorldPosition(x, y, z+height)
                        if(sx) and (sy) then
                            local distanceBetweenPoints = getDistanceBetweenPoints3D(x, y, z, x2, y2, z2)
                            if(distanceBetweenPoints < distance) then
                                dxDrawMaterialLine3D(x, y, z+1+height-(distanceBetweenPoints/distance), x, y, z+height, Image, width-(distanceBetweenPoints/distance), tocolor(R or 255, G or 255, B or 255, alpha or 255))
                            end
                        end
                end
        end

</section>
-   Original author: *Has\[S\]oN*.
-   Skype: *hassan.saad2000*

Example \#1
-----------

This example creates an image on a random ped in the Grove street.

<section name="Client" class="client" show="true">
    randomPed = createPed(285,2506.83423,-1684.89941,13.55648)
    tag = dxCreateTexture("crown.png")
     
    addEventHandler("onClientPreRender", root,
    function()
    dxDrawImageOnElement(randomPed,tag)
    end)

</section>
Example \#2
-----------

This example creates an image on all the vehicles in the game.

<section name="Client" class="client" show="true">
    local tag = dxCreateTexture("bike.png")
     
    addEventHandler("onClientPreRender", root,
    function()
    for k,v in ipairs(getElementsByType("vehicle")) do
    dxDrawImageOnElement(v,tag)
    end
    end) 

</section>
See also
--------
