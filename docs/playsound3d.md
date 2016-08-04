Creates a [sound](/docs/sound.md "wikilink") [element](/element.md "wikilink") in the GTA world and plays it immediately after creation for the local player. [setElementPosition](/setElementPosition.md "wikilink") can be used to move the [sound](/sound.md "wikilink") element around after it has been created. Remember to use [setElementDimension](/setElementDimension.md "wikilink") after creating the sound to play it outside of dimension 0.

Syntax
------

``` lua
 )
```

``` lua
 )
```

### Required Arguments

-   **soundPath:** the [filepath](/docs/filepath.md "wikilink") to the sound file you want to play. (Sound file has to be predefined in the [meta.xml](/meta.xml.md "wikilink") file with <file /> tag. And also can use url instead of [filepath](/filepath.md "wikilink") )
-   **soundURL:** the URL. (In this version the file does not has to be predefined in the [meta.xml](/docs/meta.xml.md "wikilink") )
-   **x:** a [floating](/docs/float.md "wikilink") point number representing the X coordinate on the map.
-   **y:** a [floating](/docs/float.md "wikilink") point number representing the Y coordinate on the map.
-   **z:** a [floating](/docs/float.md "wikilink") point number representing the Z coordinate on the map.

### Optional Arguments

-   **looped:** A [boolean](/docs/boolean.md "wikilink") representing whether the sound will be looped. To loop the sound, use *true*.

### Returns

Returns a [sound](/docs/sound.md "wikilink") [element](/element.md "wikilink") if the sound was successfully created, *false* otherwise.

Example
-------

This example creates a looping sound within a pizza shop. The pizza shop is in san fierro near pier 69

<section name="Example" class="client" show="true">
``` lua
function onResourceStart()
    local sound = playSound3D("sounds/song.mp3", 373.14, -125.21, 1001, true) 
end
addEventHandler("onClientResourceStart", resourceRoot, onResourceStart)
```

</section>
This example play internet radio in groove street.

<section name="Example 2" class="client" show="true" >
``` lua
addEventHandler( 'onClientResourceStart', resourceRoot,
    function( )
        local uSound = playSound3D( 'http://193.34.51.25:80', 2498, -1659, 12 ) 
        setSoundMaxDistance( uSound, 100 )
    end
)
```

</section>
See Also
--------

[AR:playSound3D](/docs/ar:playsound3d.md "wikilink") [DE:playSound3D](/DE:playSound3D.md "wikilink") [RU:playSound3D](/RU:playSound3D.md "wikilink")
