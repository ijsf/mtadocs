**Just use getElementPosition, and getZoneName(position, true)** This function retrieves player/ped/element city

Syntax
------

``` lua
string getPlayerCity(element theElement [, string state = "short" ] )
```

#### Required Arguments

-   **theElement**: The element you want to get city of

#### Optional Arguments

-   **state**: The state \[“long”, “short”\]

Returns
-------

Returns a string containing the player city, example: LS for short, Los Santos for long.

Code
----

``` lua
LSzones = {["Los Santos"]=true, ["Red County"]=true, ["Flint County"]=true}
SFzones = {["San Fierro"]=true, ["Whetstone"]=true, ["Tierra Robada"]=true}
LVzones = {["Las Venturas"]=true, ["Bone County"]=true}
function getPlayerCity(element, state)
    assert(isElement(element), "Bad argument @ getPlayerCity [expected element at argument one, got "..tostring(element).."]")
    if not state then state = "short" end
    px, py, pz = getElementPosition(element)
    if LSzones[getZoneName(px, py, pz, true)] and state == "long" then return "Los Santos"
    elseif LSzones[getZoneName(px, py, pz, true)] and state == "short" then return "LS" end
    if SFzones[getZoneName(px, py, pz, true)] and state == "long" then return "San Fierro"
    elseif SFzones[getZoneName(px, py, pz, true)] and state == "short" then return "SF" end
    if LVzones[getZoneName(px, py, pz, true)] and state == "long" then return "Las Venturas" 
    elseif LVzones[getZoneName(px, py, pz, true)] and state == "short" then return "LV" end
end
```

Example
-------

<section name="Server-side example" class="server" show="true">
This example outputs the city of a given playername and a state:

``` lua
addCommandHandler("getcityof",
    function(playerSource, command, targetName, stateName)
        target = getPlayerFromName(targetName)
        state = tostring(stateName)
        if not state then state == "short" end
        if target and state then
            outputChatBox("Player: "..getPlayerName(target).." | City: "..getPlayerCity(target, state), playerSource, 0, 255, 0)
            elseif not target or not state then
                outputChatBox("* USAGE: /getcityof [playername] [state]", playerSource, 255, 0, 0)
        end
    end)
```

</section>
See Also
--------
