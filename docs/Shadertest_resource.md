Example resource for testing [shaders](/docs/shader.md "wikilink")

File layout:

`   shadertest`
`       meta.xml`
`       clientscript.lua`
`       clientshader.fx`
`       hurry.png`

meta.xml contains this: <code lang="xml"> <meta>

<script src="clientscript.lua" type="client" />
`   `<file src="clientshader.fx" type="client" />
`   `<file src="hurry.png" type="client" />

</meta>

</syntaxhighlight>
clientscript.lua contains this:

``` lua
addEventHandler("onClientResourceStart", resourceRoot,
    function()
        myShader,tecName = dxCreateShader( "clientshader.fx" )
        myImage = dxCreateTexture( "hurry.png" )
        if myShader and myImage then
            dxSetShaderValue( myShader, "tex0", myImage )
            outputChatBox( "Shader using techinque " .. tecName )
        else
            outputChatBox( "Problem - use: debugscript 3" )
        end
    end
)

addEventHandler( "onClientRender", root,
    function()
        if myShader then
             dxDrawImage( 200, 300, 400, 200, myShader, 0, 0, 0, tocolor(255,255,0) )
        end
   end
)
```

clientshader.fx contains this:

        // Insert your fabulous crap here

hurry.png is copied from the race resource. i.e. **race/img/hurry.png**
