<lowercasetitle/>

This useful client function draws a text on any element you choose.

Syntax
------

``` Lua
 )
```

[thumb|Example of how it should looks like.|284x230px](/docs/image:dxdrawtextonelement.png.md "wikilink")

Required arguments
------------------

-   *TheElement*: The element you want to draw the text on it.
-   *text*: The text you want.

Optional arguments
------------------

-   *height*: The height of the text, it's 1 by default.
-   *distance*: The distance you will be able to view the text from, it's 20 by default.
-   *R*: The Red color code (0-255), it's 255 by default.
-   *G*: The Green color code (0-255), it's 255 by default.
-   *B*: The Blue color code (0-255), it's 255 by default.
-   *alpha*: The alpha of the text, it's 255 by default.
-   *size*: The size of the text, it's 1 by default.
-   *font*: Either a custom [DX font](/docs/dx_font.md "wikilink") element or the name of a built-in DX font:

It's arial by default.

-   **checkBuildings:** Allow the line of sight to be blocked by GTA's internally placed buildings, i.e. the world map.
-   **checkVehicles:** Allow the line of sight to be blocked by [vehicles](/docs/vehicle.md "wikilink").
-   **checkPeds:** Allow the line of sight to be blocked by peds, i.e. [players](/docs/player.md "wikilink").
-   **checkObjects:** Allow the line of sight to be blocked by [objects](/docs/object.md "wikilink").
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
    function dxDrawTextOnElement(TheElement,text,height,distance,R,G,B,alpha,size,font,checkBuildings,checkVehicles,checkPeds,checkDummies,seeThroughStuff,ignoreSomeObjectsForCamera,ignoredElement)
                    local x, y, z = getElementPosition(TheElement)
                    local x2, y2, z2 = getElementPosition(localPlayer)
                    local distance = distance or 20
                    local height = height or 1
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
                                dxDrawText(text, sx+2, sy+2, sx, sy, tocolor(R or 255, G or 255, B or 255, alpha or 255), (size or 1)-(distanceBetweenPoints / distance), font or "arial", "center", "center")
                end
            end
        end
    end

</section>
-   Original author: *Has\[S\]oN*.
-   Skype: *hassan.saad2000*

Example \#1
-----------

This example creates a text on a random ped in the Grove street.

<section name="Client" class="client" show="true">
    randomPed = createPed(285,2476.91406,-1665.31799,13.32435)

    addEventHandler("onClientRender", getRootElement(), 
    function ()
    dxDrawTextOnElement(randomPed,"SWATTEAM Officer",1,20,0,0,255,255,1,"pricedown")
    end)

</section>
Example \#2
-----------

This example creates a text 'HassoN' on all the players are in a team named HassoN.

<section name="Client" class="client" show="true">
    addEventHandler("onClientRender", getRootElement(), 
    function ()
    for k,v in ipairs(getElementsByType("player")) do
            if getPlayerTeam(v) == getTeamFromName("HassoN") then
                if v == localPlayer then return end
                dxDrawTextOnElement(v,"HassoN",1,20,0,0,255,255,1,"arial")
            end
        end
    end)

</section>
See also
--------
