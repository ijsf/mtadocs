**This article concerns the note left in [attachElements](/attachElements.md "wikilink").**

Problem
-------

The offset coordinates reflect the object space, not the world space. This means that you cannot simply visualize the attachment in the map editor and calculate the offsets between the 2 sets of world coordinates for “theElement” and “theAttachToObject”.

For example, if “theAttachToElement” has XYZ rotations, then “theElement” will inherit these rotations. The specified rotation offsets will then be performed from these starting rotation points. Simply put, “theElement” will be rotated twice.

Solution
--------

The following code shows how to use offsets calculated in the map editor with 'attachElements':

    addEventHandler( "onResourceStart", resourceRoot,
        function()
            -- Postion and rotations from the map editor:
            local mainPos = { -756, 995, 14 }
            local mainRot = { 0, 0, 90 }            -- Two rotations are zero. See note in attachRotationAdjusted

            local subPos = { -756, 999, 24 }
            local subRot = { 89, 0, 177 }           -- One rotation is zero. See note in attachRotationAdjusted

            -- Create the objects
            mainObject = createObject ( 17050, mainPos[1], mainPos[2], mainPos[3], mainRot[1], mainRot[2], mainRot[3] )
            subObject = createVehicle ( 519, subPos[1], subPos[2], subPos[3], subRot[1], subRot[2], subRot[3] )

            -- Attach so they look like what they do in the map editor
            attachRotationAdjusted ( subObject, mainObject )
        end
    )


    function attachRotationAdjusted ( from, to )
        -- Note: Objects being attached to ('to') should have at least two of their rotations set to zero
        --       Objects being attached ('from') should have at least one of their rotations set to zero
        -- Otherwise it will look all funny

        local frPosX, frPosY, frPosZ = getElementPosition( from )
        local frRotX, frRotY, frRotZ = getElementRotation( from )
        local toPosX, toPosY, toPosZ = getElementPosition( to )
        local toRotX, toRotY, toRotZ = getElementRotation( to )
        local offsetPosX = frPosX - toPosX
        local offsetPosY = frPosY - toPosY
        local offsetPosZ = frPosZ - toPosZ
        local offsetRotX = frRotX - toRotX
        local offsetRotY = frRotY - toRotY
        local offsetRotZ = frRotZ - toRotZ

        offsetPosX, offsetPosY, offsetPosZ = applyInverseRotation ( offsetPosX, offsetPosY, offsetPosZ, toRotX, toRotY, toRotZ )

        attachElements( from, to, offsetPosX, offsetPosY, offsetPosZ, offsetRotX, offsetRotY, offsetRotZ )
    end


    function applyInverseRotation ( x,y,z, rx,ry,rz )
        -- Degress to radians
        local DEG2RAD = (math.pi * 2) / 360
        rx = rx * DEG2RAD
        ry = ry * DEG2RAD
        rz = rz * DEG2RAD

        -- unrotate each axis
        local tempY = y
        y =  math.cos ( rx ) * tempY + math.sin ( rx ) * z
        z = -math.sin ( rx ) * tempY + math.cos ( rx ) * z

        local tempX = x
        x =  math.cos ( ry ) * tempX - math.sin ( ry ) * z
        z =  math.sin ( ry ) * tempX + math.cos ( ry ) * z

        tempX = x
        x =  math.cos ( rz ) * tempX + math.sin ( rz ) * y
        y = -math.sin ( rz ) * tempX + math.cos ( rz ) * y

        return x, y, z
    end
