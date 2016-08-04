This function returns one of the child elements of a given parent element. The child element is selected by its index (0 for the first child, 1 for the second and so on).

Syntax
------

``` lua
element getElementChild ( element parent, int index ) 
```

### Required Arguments

-   **parent:** the element above the one to be returned in the hierarchy.
-   **index:** the element's index (0 for the first element, 1 for the second, etc).

### Returns

Returns the requested element if it exists, or *false* if it doesn't.

Example
-------

If the .map file contains:

``` xml
<team1 id="red">
    <base name="Mountain Top" />
    <base name="Docks" />
    <base name="Airport" />
</team1>
```

This outputs the name of the specified base. For example: 'teamBase 0' for the first base.

``` lua
function showTeamBase(thePlayer, command, index)
    local theTeam = getElementByID("red")                   -- get the team element
    local base = getElementChild(theTeam, tonumber(index))  -- get the Child of the element, based on the 'index' the player specified.
    if (base ~= false) then                                 -- if the base exists
        outputChatBox("Team base " .. index .. ": " .. getElementData(base, "name"), thePlayer)  -- output it to the player
    else
        outputChatBox("Base not found.", thePlayer)
    end
end
addCommandHandler("teamBase", showTeamBase)
```

Note that if there are other child elements, you'd have to check whether the element is a base with the [getElementType](/getElementType.md "wikilink") function. For example: 'teamBase 3' would output 'Team Base 3: Factory' with the .map file below, even though it's no base.

``` xml
<team1 id="red">
    <base name="Mountain Top" />
    <base name="Docks" />
    <base name="Airport" />
    <target name="Factory" />
</team1>
```

See Also
--------
