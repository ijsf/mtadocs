Returns the 3D world coordinates of a specific bone of a given ped.

Syntax
------

``` lua
float float float getPedBonePosition ( ped thePed, int bone )
```

### Required Arguments

-   **thePed:** the ped you want to inspect.
-   **bone:** the number of the bone to get the position of.

[thumb|Bone numbers](/docs/Image:Bones.jpg.md "wikilink")

<div style="border: 3px red solid; margin-bottom:3px; padding-left:5px;">
-   **1:** BONE\_PELVIS1
-   **2:** BONE\_PELVIS
-   **3:** BONE\_SPINE1
-   **4:** BONE\_UPPERTORSO
-   **5:** BONE\_NECK
-   **6:** BONE\_HEAD2
-   **7:** BONE\_HEAD1
-   **8:** BONE\_HEAD
-   **21:** BONE\_RIGHTUPPERTORSO
-   **22:** BONE\_RIGHTSHOULDER
-   **23:** BONE\_RIGHTELBOW
-   **24:** BONE\_RIGHTWRIST
-   **25:** BONE\_RIGHTHAND
-   **26:** BONE\_RIGHTTHUMB
-   **31:** BONE\_LEFTUPPERTORSO
-   **32:** BONE\_LEFTSHOULDER
-   **33:** BONE\_LEFTELBOW
-   **34:** BONE\_LEFTWRIST
-   **35:** BONE\_LEFTHAND
-   **36:** BONE\_LEFTTHUMB
-   **41:** BONE\_LEFTHIP
-   **42:** BONE\_LEFTKNEE
-   **43:** BONE\_LEFTANKLE
-   **44:** BONE\_LEFTFOOT
-   **51:** BONE\_RIGHTHIP
-   **52:** BONE\_RIGHTKNEE
-   **53:** BONE\_RIGHTANKLE
-   **54:** BONE\_RIGHTFOOT

</div>
### Returns

Returns the x, y, z world position of the bone.

Example
-------

This example renders name tags above a player's head bone.

    addEventHandler( "onClientRender",root,
       function( )
          local px, py, pz, tx, ty, tz, dist
          px, py, pz = getCameraMatrix( )
          for _, v in ipairs( getElementsByType 'player' ) do
             tx, ty, tz = getElementPosition( v )
             dist = math.sqrt( ( px - tx ) ^ 2 + ( py - ty ) ^ 2 + ( pz - tz ) ^ 2 )
             if dist < 30.0 then
                if isLineOfSightClear( px, py, pz, tx, ty, tz, true, false, false, true, false, false, false,localPlayer ) then
                   local sx, sy, sz = getPedBonePosition( v, 5 )
                   local x,y = getScreenFromWorldPosition( sx, sy, sz + 0.3 )
                   if x then -- getScreenFromWorldPosition returns false if the point isn't on screen
                    dxDrawText( getPlayerName( v ), x, y, x, y, tocolor(150, 50, 0), 0.85 + ( 15 - dist ) * 0.02, "bankgothic" )
                   end
                end
             end
          end
       end
    )

Example 2
---------

This one draw all local player's bones

    addEventHandler('onClientRender', root, function()
        for bone = 1, 54 do
         local bonePos = {getPedBonePosition(localPlayer, bone)}
            if bonePos[1] then
             local screen = {getScreenFromWorldPosition(unpack(bonePos))}
                if screen[1] then
                 dxDrawText(''..bone, screen[1], screen[2])
                end
            end
        end
    end)

See Also
--------

[ru:GetPedBonePosition](/docs/ru:GetPedBonePosition.md "wikilink")
