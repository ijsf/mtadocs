### Below has not been tested properly, and may have mistakes

    //
    //-- Stuff for reading depth buffer
    //
    //-- Reading depth buffer supported by:
    //--   NVidia - from GeForce 6 (2004)
    //--   Radeon - from 9500      (2002)
    //--   Intel  - from G45       (2008)
    //
    //-- Sources:
    //-- http://obge.paradice-insight.us/wiki/Internals_%28Effects%29
    //-- http://www.gamasutra.com/blogs/BranoKemen/20090812/2725/Logarithmic_Depth_Buffer.php
    //-- http://mynameismjp.wordpress.com/2009/05/05/reconstructing-position-from-depth-continued/
    //-- 

    //-- These two are set by MTA
    texture gDepthBuffer : DEPTHBUFFER;
    matrix gProjectionMainScene : PROJECTION_MAIN_SCENE;

    sampler SamplerDepth = sampler_state
    {
        Texture     = (gDepthBuffer);
        AddressU    = Clamp;
        AddressV    = Clamp;
    };

    //---------------------------------------------------------------------
    // Structure of data sent to the pixel shader ( from the vertex shader )
    //---------------------------------------------------------------------
    struct PSInput
    {
      float4 Position : POSITION0;
      float2 TexCoord0 : TEXCOORD0;
    };

    //-----------------------------------------------------------------------------
    //-- Get value from the depth buffer
    //-- Uses define set at compile time to handle RAWZ special case (which will use up a few more slots)
    //-----------------------------------------------------------------------------
    float FetchDepthBufferValue( float2 uv )
    {
        float4 texel = tex2D(SamplerDepth, uv);
    #if IS_DEPTHBUFFER_RAWZ
        float3 rawval = floor(255.0 * texel.arg + 0.5);
        float3 valueScaler = float3(0.996093809371817670572857294849, 0.0038909914428586627756752238080039, 1.5199185323666651467481343000015e-5);
        return dot(rawval, valueScaler / 255.0);
    #else
        return texel.r;
    #endif
    }

    //-----------------------------------------------------------------------------
    //-- Use the last scene projecion matrix to linearize the depth value a bit more
    //-----------------------------------------------------------------------------
    float Linearize(float posZ)
    {
        return gProjectionMainScene[3][2] / (posZ - gProjectionMainScene[2][2]);
    }


    //-----------------------------------------------------------------------------
    //-- Name: PS_Example
    //-- Type: Pixel shader
    //-- Desc: Calculates the pixel color based on texture lookup and interpolated vertex color
    //-----------------------------------------------------------------------------
    float4 PS_Example( PSInput In ) : COLOR
    {
        float BufferValue = FetchDepthBufferValue( In.TexCoord0.xy );
        float Depth = Linearize( BufferValue );

        //-- Multiply Depth to get the spread you want
        Depth *= 0.1f;

        //-- Show depth as green
        float4 OutColor = 0;
        OutColor.g = Depth;
        OutColor.a = 1;
        return OutColor;
    }



    //-----------------------------------------------------------------------------
    //-- Techniques
    //-----------------------------------------------------------------------------

    //
    //-- Use any readable depthbuffer format
    //
    technique yes_effect
    {
        pass P0
        {
            PixelShader  = compile ps_2_0 PS_Example();
        }
    }


    //
    //-- If no depthbuffer support, do nothing
    //
    technique no_effect
    {
        pass P0
        {
        }
    }
