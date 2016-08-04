This function loads an animation library (IFP) file into GTA.

-   This function **does not replace** the default animations yet.
-   To use this correctly, you need to use an IFP file with **new** animation blocks with different names than existing ones.

Be sure to transfer your IFP file by including it in the meta file.

Syntax
------

``` lua
ifp engineLoadIFP ( string ifp_file ) 
```

### Required Arguments

-   **ifp\_file:** The [filepath](/docs/filepath.md "wikilink") to the IFP file you want to load

### Returns

Returns an [IFP](/docs/IFP.md "wikilink") element if the IFP file loaded, *false* otherwise.

Example
-------

<section name="animation.lua" class="client" show="true">
``` lua
function setanimation()
  if engineLoadIFP("data/ani.ifp") then
    setPedAnimation(getLocalPlayer(), "ANIMATIONBLOCK", "animation1")
  end
end

addCommandHandler("animation", setanimation)
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
