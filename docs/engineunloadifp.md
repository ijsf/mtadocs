This function unloads an animation library loaded by [engineLoadIFP](/docs/engineloadifp.md "wikilink").

Syntax
------

``` lua
bool engineLoadIFP ( element ifp ) 
```

### Required Arguments

-   **ifp:** The IFP [element](/docs/element.md "wikilink") loaded by [engineLoadIFP](/docs/engineloadifp.md "wikilink") to unload.

### Returns

Returns *true* if the IFP file has been unloaded succesfully, *false* otherwise.

Example
-------

<section name="animation.lua" class="client" show="true">
``` lua
local localPlayer = getLocalPlayer()
local ifp = nil

function setanimation()
  ifp = engineLoadIFP("data/ani.ifp")
  if ifp then
    setPedAnimation(localPlayer, "ANIMATIONBLOCK", "animation1")
  end
end

addCommandHandler("animation", setanimation)

function stopanimation()
  if ifp then
    engineUnloadIFP(ifp)
    setPedAnimation(localPlayer)
  end
end

addCommandHandler("stopanimation", stopanimation)
```

</section>
<section name="meta.xml" class="server" show="true">
    <meta>
      <info author="lukry" version="1.0" type="script" />
      <script src="animation.lua" type="client" />
      <file src="data/ani.ifp" />
    </meta>

</section>
See Also
--------
