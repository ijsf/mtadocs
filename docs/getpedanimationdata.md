This function is used to return the animation data of a [player](/docs/player.md "wikilink") or [ped](/ped.md "wikilink") that was set using [setPedAnimation](/setPedAnimation.md "wikilink").

Syntax
------

``` lua
string getPedAnimationData ( ped thePed )
```

### Required Arguments

-   **thePed:** the player or ped you want to get the animation data of.

### Returns

Returns 2 [strings](/docs/string.md "wikilink") containing information about [animations](/animations.md "wikilink"). These keys are present below :

-   **name:** string - name of the animation
-   **block\_name:** string - name of animation block

### Example

This example adds a command to get the local player [animation](/docs/animations.md "wikilink") data.

``` lua
function animData()
     local data = getPedAnimationData(localPlayer)
     if data then
          outputChatBox(data)
     else
          outputChatBox("Sorry, but you're not doing thing!")
     end
end
addCommandHandler("getAnimData",animData)
```

Requirements
------------

See Also
--------
