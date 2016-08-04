The shader class represents a Microsoft HLSL Effect File(.fx) loaded by the client, which can be used instead of a texture when calling [dxDrawImage](/docs/dxdrawimage.md "wikilink")

The element type of this class is **“shader”**.

How HLSL Effect Files file integrate into MTA:SA
------------------------------------------------

Note: This page assumes you know what an Effect File and HLSL is. If not, you better do some research first.

You can use this [shadertest resource](/docs/shadertest_resource.md "wikilink") to try the examples below. Copy the effect source from the code boxes into **shadertest/clientshader.fx** and (re)start shadertest to see the output.

After you've done all that, (or maybe before if glancing below is making you panic), visit [some more shader resource examples](/docs/shader_examples.md "wikilink").

### Techniques

Effect Files usually contain several techniques, but for simplicity, MTA will only use the first technique that will run correctly on the clients hardware. So, for any given Effect File, put your high end techniques first, and the simplest ones last. That way, players with good hardware get the best technique applied, and players with older hardware get at least something.

### Simplest

Here is the contents of an Effect File with one technique which should work on all hardware:

    //-- Declare the textures. These are set using dxSetShaderValue( shader, "Tex0", texture )
    texture Tex0;
    texture Tex1;

    //-- Very simple technique
    technique simple
    {
        pass P0
        {
            //-- Set up texture stage 0
            Texture[0] = Tex0;
            ColorOp[0] = SelectArg1;
            ColorArg1[0] = Texture;
            AlphaOp[0] = SelectArg1;
            AlphaArg1[0] = Texture;
                
            //-- Disable texture stage 1
            ColorOp[1] = Disable;
            AlphaOp[1] = Disable;
        }
    }

It doesn't use vertex or pixel shaders, only standard D3D render states. Confusing reference of all the states you can set is here: <http://msdn.microsoft.com/en-us/library/bb173347%28v=VS.85%29.aspx>

### Not so simple

Here is an Effect File containing a vertex and pixel shader:

    //-- Declare the textures. These are set using dxSetShaderValue( shader, "Tex0", texture )
    texture Tex0;
    texture Tex1;

    //-- Declare a user variable. This can be set using dxSetShaderValue( shader, "PositionOfCheese", 1, 2, 3 )
    float3 PositionOfCheese;

    //-- These variables are set automatically by MTA
    float4x4 World;
    float4x4 View;
    float4x4 Projection;
    float4x4 WorldViewProjection;
    float Time;


    //---------------------------------------------------------------------
    //-- Sampler for the main texture (needed for pixel shaders)
    //---------------------------------------------------------------------
    sampler Sampler0 = sampler_state
    {
        Texture = (Tex0);
    };


    //---------------------------------------------------------------------
    //-- Structure of data sent to the vertex shader
    //---------------------------------------------------------------------
    struct VSInput
    {
        float3 Position : POSITION;
        float4 Diffuse  : COLOR0;
        float2 TexCoord : TEXCOORD0;
    };

    //---------------------------------------------------------------------
    //-- Structure of data sent to the pixel shader ( from the vertex shader )
    //---------------------------------------------------------------------
    struct PSInput
    {
      float4 Position : POSITION0;
      float4 Diffuse  : COLOR0;
      float2 TexCoord : TEXCOORD0;
    };


    //-----------------------------------------------------------------------------
    //-- VertexShaderExample
    //--  1. Read from VS structure
    //--  2. Process
    //--  3. Write to PS structure
    //-----------------------------------------------------------------------------
    PSInput VertexShaderExample(VSInput VS)
    {
        PSInput PS = (PSInput)0;

        //-- Transform vertex position (You nearly always have to do something like this)
        PS.Position = mul(float4(VS.Position, 1), WorldViewProjection);

        //-- Copy the color and texture coords so the pixel shader can use them
        PS.Diffuse = VS.Diffuse;
        PS.TexCoord = VS.TexCoord;

        return PS;
    }


    //-----------------------------------------------------------------------------
    //-- PixelShaderExample
    //--  1. Read from PS structure
    //--  2. Process
    //--  3. Return pixel color
    //-----------------------------------------------------------------------------
    float4 PixelShaderExample(PSInput PS) : COLOR0
    {
        //-- Modify the texture coord to make the image look all wobbly
        PS.TexCoord.y += sin(PS.TexCoord.y * 100 + Time * 10) * 0.03;

        //-- Grab the pixel from the texture
        float4 finalColor = tex2D(Sampler0, PS.TexCoord);

        //-- Apply color tint
        finalColor = finalColor * PS.Diffuse;

        return finalColor;
    }


    //-----------------------------------------------------------------------------
    //-- Techniques
    //-----------------------------------------------------------------------------

    //--
    //-- MTA will try this technique first:
    //--
    technique complercated
    {
        pass P0
        {
            VertexShader = compile vs_2_0 VertexShaderExample();
            PixelShader  = compile ps_2_0 PixelShaderExample();
        }
    }

    //--
    //-- And if the preceding technique will not validate on
    //-- the players computer, MTA will try this one:
    //--
    technique simple
    {
        pass P0
        {
            //-- Set up texture stage 0
            Texture[0] = Tex0;
            ColorOp[0] = SelectArg1;
            ColorArg1[0] = Texture;
            AlphaOp[0] = SelectArg1;
            AlphaArg1[0] = Texture;
                
            //-- Disable texture stage 1
            ColorOp[1] = Disable;
            AlphaOp[1] = Disable;
        }
    }

Technique 'complercated' will be used if the computer supports Shader Model 2, otherwise technique 'simple' will be used. Comments in the source explain what MTA does and where.

### Misc

Points to remember when switching between editing lua and .fx files:

-   HLSL statements often end with a ; (semi-colon)
-   HLSL indices start from 0 (where as Lua usually starts from 1)
-   HLSL compile errors can be viewed by typing 'debugscript 3' into the client console

Shaders for world textures
--------------------------

Here are a couple of examples of shaders to use when replacing world textures with [engineApplyShaderToWorldTexture](/docs/engineapplyshadertoworldtexture.md "wikilink")

### Simple

This shader just replaces the texture and allows GTA to control all the render states.

    //-- Declare the texture. These are set using dxSetShaderValue( shader, "Tex0", texture )
    texture Tex0;

    technique simple
    {
        pass P0
        {
            //-- Set up texture stage 0
            Texture[0] = Tex0;

            //-- Leave the rest of the states to the default settings
        }
    }

===Not so simple=== This shader can be used as a base for replacing a world texture if you intend to add some fancy effect. It uses [<http://nightly.mtasa.com/files/shaders/mta-helper.fx> mta-helper.fx](/docs/http-//nightly.mtasa.com/files/shaders/mta-helper.fx_mta-helper.fx.md "wikilink") to handle consistent naming of the preset shader settings (gWorld, gTexture0 etc.)
***mta-helper.fx*** also contains some helpful functions which calculate GTA lighting.

    //-----------------------------------------------------------------------
    //-- Settings
    //-----------------------------------------------------------------------
    texture Tex0;   //-- Replacement texture


    //---------------------------------------------------------------------
    // Include some common stuff
    //---------------------------------------------------------------------
    #include "mta-helper.fx"


    //-----------------------------------------------------------------------
    //-- Sampler for the new texture
    //-----------------------------------------------------------------------
    sampler Sampler0 = sampler_state
    {
        Texture = (Tex0);
    };


    //-----------------------------------------------------------------------
    //-- Structure of data sent to the vertex shader
    //-----------------------------------------------------------------------
    struct VSInput
    {
        float3 Position : POSITION0;
        float3 Normal : NORMAL0;
        float4 Diffuse : COLOR0;
        float2 TexCoord : TEXCOORD0;
    };

    //-----------------------------------------------------------------------
    //-- Structure of data sent to the pixel shader ( from the vertex shader )
    //-----------------------------------------------------------------------
    struct PSInput
    {
        float4 Position : POSITION0;
        float4 Diffuse : COLOR0;
        float2 TexCoord : TEXCOORD0;
    };


    //--------------------------------------------------------------------------------------------
    //-- VertexShaderFunction
    //--  1. Read from VS structure
    //--  2. Process
    //--  3. Write to PS structure
    //--------------------------------------------------------------------------------------------
    PSInput VertexShaderFunction(VSInput VS)
    {
        PSInput PS = (PSInput)0;

        //-- Calculate screen pos of vertex
        PS.Position = mul(float4(VS.Position, 1), gWorldViewProjection);

        //-- Pass through tex coord
        PS.TexCoord = VS.TexCoord;

        //-- Calculate GTA lighting for buildings
        PS.Diffuse = MTACalcGTABuildingDiffuse( VS.Diffuse );
        //--
        //-- NOTE: The above line is for GTA buildings.
        //-- If you are replacing a vehicle texture, do this instead:
        //--
        //--      // Calculate GTA lighting for vehicles
        //--      float3 WorldNormal = MTACalcWorldNormal( VS.Normal );
        //--      PS.Diffuse = MTACalcGTAVehicleDiffuse( WorldNormal, VS.Diffuse );

        return PS;
    }


    //--------------------------------------------------------------------------------------------
    //-- PixelShaderFunction
    //--  1. Read from PS structure
    //--  2. Process
    //--  3. Return pixel color
    //--------------------------------------------------------------------------------------------
    float4 PixelShaderFunction(PSInput PS) : COLOR0
    {
        //-- Get texture pixel
        float4 texel = tex2D(Sampler0, PS.TexCoord);

        //-- Apply diffuse lighting
        float4 finalColor = texel * PS.Diffuse;

        return finalColor;
    }


    //--------------------------------------------------------------------------------------------
    //-- Techniques
    //--------------------------------------------------------------------------------------------
    technique tec
    {
        pass P0
        {
            VertexShader = compile vs_2_0 VertexShaderFunction();
            PixelShader = compile ps_2_0 PixelShaderFunction();
        }
    }

    //-- Fallback
    technique fallback
    {
        pass P0
        {
            //-- Replace texture
            Texture[0] = Tex0;

            //-- Leave the rest of the states to the default settings
        }
    }

The above code as it stands will calculate the correct lighting for GTA buildings. If you are replacing a vehicle, change:

        //-- Calculate GTA lighting for buildings
        PS.Diffuse = MTACalcGTABuildingDiffuse( VS.Diffuse );

to:

        //-- Calculate GTA lighting for vehicles
        float3 WorldNormal = MTACalcWorldNormal( VS.Normal );
        PS.Diffuse = MTACalcGTAVehicleDiffuse( WorldNormal, VS.Diffuse );

==Multiple pass shaders== To do more than one pass, add **pass** blocks like this:

    //-- Declare the texture. These are set using dxSetShaderValue( shader, "Tex0", texture )
    texture Tex0;

    technique simple
    {
        pass P0
        {
            // First pass
            Texture[0] = Tex0;
        }
        pass P1
        {
            // Second pass
            SrcBlend = Add;
            DestBlend = One;
        }
        pass P2
        {
            // Third pass
            SrcBlend = InvDestColor;
            DestBlend = InvSrcColor;
        }
    }

==Related scripting functions==

### Client

[Category:Element Types](/docs/category-element_types.md "wikilink")
