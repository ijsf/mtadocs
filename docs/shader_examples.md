This page contains some example shader resources to try. If you are looking to make your own, please be sure to read about the [shader element](/docs/shader.md "wikilink") as well.

Road shine
----------

[200px|thumb|left|Road shine](/docs/image:roadshinescreen.jpg.md "wikilink")

<table border=0>
<tr>
<td valign=top height=170>
[Download shader\_roadshine.zip](http://nightly.mtasa.com/files/shaders/shader_roadshine.zip)   *Requires Shader Model 2 graphics card*
This resource creates a light reflection effect on the ground (looks best when moving). It uses a custom flag in the effect file to generate [surface normals](http://en.wikipedia.org/wiki/Surface_normal) for the ground model:

    int CUSTOMFLAGS
    <
        string createNormals = "yes";
    >;

Surface normals are not usually present in the ground and building models, but are useful for creating lighting effects such as these.

</td>
</tr>
</table>
Road shine 2
------------

[200px|thumb|left|Road shine 2](/docs/image:roadshine2screen.jpg.md "wikilink")

<table border=0>
<tr>
<td valign=top height=170>
[Download shader\_roadshine2.zip](http://nightly.mtasa.com/files/shaders/shader_roadshine2.zip)   *Requires Shader Model 2 graphics card*
Bit more complicated than the first Road shine, as it tracks the sun or moon to calculate the position of the highlight. The effect can be hard to see depending on the time of day.
Best used with the play resource as the model it modifies is near the initial spawn point.

</td>
</tr>
</table>
Road shine 3 (Deluxe edition)
-----------------------------

[200px|thumb|left|Road shine 3](/docs/image:roadshine3screen.jpg.md "wikilink")

<table border=0>
<tr>
<td valign=top height=170>
[Download shader\_roadshine3.zip](http://nightly.mtasa.com/files/shaders/shader_roadshine3.zip)   *Requires Shader Model 2 graphics card*
This resource shows how to:

-   Stop a wild card match shader from being applied to certain world textures.
-   Use isLineOfSightClear to stop an effect when something is not visible (The sun in this case).
-   Use a shader maxDrawDistance setting to avoid GPU overload.

The final effect is a faster shader with less rendering issues than the previous two road shine examples.

</td>
</tr>
</table>
UV scroll
---------

[200px|thumb|left|UV scroll](/docs/image:uvscollscreen.jpg.md "wikilink")

<table border=0>
<tr>
<td valign=top height=170>
[Download shader\_uv\_scroll.zip](http://nightly.mtasa.com/files/shaders/shader_uv_scroll.zip)
This resource scrolls a texture from left to right. It doesn't use vertex or pixels shaders, so it should work on all hardware.

</td>
</tr>
</table>
UV scripted
-----------

[200px|thumb|left|UV scripted](/docs/image:uvscriptedscreen.jpg.md "wikilink")

<table border=0>
<tr>
<td valign=top height=170>
[Download shader\_uv\_scripted.zip](http://nightly.mtasa.com/files/shaders/shader_uv_scripted.zip)
This resource controls a texture's UVs using Lua. It shows that anything is possible if you can imagine it.

</td>
</tr>
</table>
Car paint
---------

[200px|thumb|left|Car paint](/docs/image:carpaintscreen.jpg.md "wikilink")

<table border=0>
<tr>
<td valign=top height=170>
[Download shader\_car\_paint.zip](http://nightly.mtasa.com/files/shaders/shader_car_paint.zip)   *Requires Shader Model 2 graphics card*
This resource shows you how to apply a shader to the vehicle models. The shader itself is not that great, so don't get your hopes up.

</td>
</tr>
</table>
Water
-----

[200px|thumb|left|Water](/docs/image:waterscreen.jpg.md "wikilink")

<table border=0>
<tr>
<td valign=top height=170>
[Download shader\_water.zip](http://nightly.mtasa.com/files/shaders/shader_water.zip)   *Requires Shader Model 2 graphics card*
This resource applies a shader to the GTA world water. The Lua script shows how to use a timer to transfer the conventional water color setting to the shader.

</td>
</tr>
</table>
Bloom
-----

[200px|thumb|left|Bloom](/docs/image:bloomscreen.jpg.md "wikilink")

<table border=0>
<tr>
<td valign=top height=170>
[Download shader\_bloom.zip](http://nightly.mtasa.com/files/shaders/shader_bloom.zip)   *Requires Shader Model 2 graphics card*
This resource shows you how 'bounce' full screen effects using a render target pool. It uses the *onClientHUDRender* event to exclude the HUD from the effect.

</td>
</tr>
</table>
Block world
-----------

[200px|thumb|left|Block world](/docs/image:blockworld.jpg.md "wikilink")

<table border=0>
<tr>
<td valign=top height=170>
[Download shader\_block\_world.zip](http://nightly.mtasa.com/files/shaders/shader_block_world.zip)   *Requires Shader Model 2 graphics card*
This resource makes the textures look all blocky. It also changes colors when the 'k' key is pressed.

</td>
</tr>
</table>
Texture names
-------------

[200px|thumb|left|Texture names](/docs/image:texnames.jpg.md "wikilink")

<table border=0>
<tr>
<td valign=top height=170>
[Download shader\_tex\_names.zip](http://nightly.mtasa.com/files/shaders/shader_tex_names.zip)
This resource is only a tool, and doesn't do anything pretty. It shows a list of the current visible texture names, and highlights the selected texture. Ideal for finding a texture name to use with [engineApplyShaderToWorldTexture](/docs/engineapplyshadertoworldtexture.md "wikilink").

num\_8 shows/hides the texture list, num\_7 and num\_9 step through the list, and 'k' copies the current texture name to the clipboard.

</td>
</tr>
</table>
Skid marks
----------

[200px|thumb|left|Skid marks](/docs/image:skidmarks.jpg.md "wikilink")

<table border=0>
<tr>
<td valign=top height=170>
[Download shader\_skidmarks.zip](http://nightly.mtasa.com/files/shaders/shader_skidmarks.zip)   *Requires Shader Model 2 graphics card*
This resource shows you how to do multiple passes in a shader, and input different variables to the vertex shader for each pass. Use the command **/skidmarks 1-4** to see the different effects. (You have skid a car to see it!)

</td>
</tr>
</table>
HDR contrast
------------

[200px|thumb|left|HDR contrast](/docs/image:shadercontrast.jpg.md "wikilink")

<table border=0>
<tr>
<td valign=top height=170>
[Download shader\_contrast.zip](http://nightly.mtasa.com/files/shaders/shader_contrast.zip)   *Requires Shader Model 2 graphics card*
This resource applies a 'High Dynamic Range' contrast effect. It uses a 1 pixel render target to sample the whole scene, and then uses that to brighten or darken the next frame. So going into somewhere dark will automatically brighten the scene, and visa versa

</td>
</tr>
</table>
Tessellation
------------

[200px|thumb|left|Tessellation action](/docs/image:shader_flag.jpg.md "wikilink")

<table border=0>
<tr>
<td valign=top height=170>
[Download shader\_flag.zip](http://nightly.mtasa.com/files/shaders/shader_flag.zip)   *Requires Shader Model 2 graphics card*
This resource shows how to use shader tessellation to animate the shape of a dxDrawImage and use shader transform to give it a 3rd dimension.

The example has a GUI (press numpad-8) so you can fiddle with the settings.

</td>
</tr>
</table>
Radial blur
-----------

[200px|thumb|left|Radial blur](/docs/image:shader_radial_blur.jpg.md "wikilink")

<table border=0>
<tr>
<td valign=top height=170>
[Download shader\_radial\_blur.zip](http://nightly.mtasa.com/files/shaders/shader_radial_blur.zip)   *Requires Shader Model 2 graphics card*
This resource sort of looks a little bit like the GTAIV motion blur you get when you move the mouse quickly, or drive a fast car. The fast car effect is a bit more subtle than the screen shot would suggest, as it leaves the center of the screen nice and clear so you can see where you are going.

It also has the option of suspending the effect during times of low FPS. Check the two settings at the top of ***c\_radial\_blur.lua***.
The file ***c\_switch.lua*** contains information on how to toggle the effect from another resource using events.

</td>
</tr>
</table>
Detail
------

[200px|thumb|left|Detail](/docs/image:shader_detail.jpg.md "wikilink")

<table border=0>
<tr>
<td valign=top height=170>
[Download shader\_detail.zip](http://nightly.mtasa.com/files/shaders/shader_detail.zip)   *Requires Shader Model 2 graphics card*
Applies a few monochrome detail textures, at various scales, to (parts of) the world.

(Not finished and probably never will be.)

</td>
</tr>
</table>
Ped morph
---------

[200px|thumb|left|Ped morph](/docs/image:pedmorphscreen.jpg.md "wikilink")

<table border=0>
<tr>
<td valign=top height=170>
[Download shader\_ped\_morph.zip](http://nightly.mtasa.com/files/shaders/shader_ped_morph.zip)   *Requires Shader Model 2 graphics card*
This resource uses a vertex shader to modify the geometry of a ped model as it is rendered.
When the resource has started, use the 'k' and 'l' keys to change morph size.

</td>
</tr>
</table>
Ped shell
---------

[200px|thumb|left|Ped shell](/docs/image:pedshellscreen.jpg.md "wikilink")

<table border=0>
<tr>
<td valign=top height=170>
[Download shader\_ped\_shell.zip](http://nightly.mtasa.com/files/shaders/shader_ped_shell.zip)   *Requires Shader Model 2 graphics card*
This resource draws a translucent effect as a shader layer. The first pass is done by GTA, and the vertex shader is only applied in the second to add the effect 'on top' of the standard output.
When the resource has started, use the 'm' key to see the shell effect.

</td>
</tr>
</table>
Hud mask
--------

[200px|thumb|left|Hud mask](/docs/image:shader_hud_mask.jpg.md "wikilink")

<table border=0>
<tr>
<td valign=top height=170>
[Download shader\_hud\_mask.zip](http://nightly.mtasa.com/files/shaders/shader_hud_mask.zip)
This resource shows how to draw a hud texture with a shape mask.

</td>
</tr>
</table>
dxDrawCircle
------------

[200px|thumb|left|dxDrawCircle](/docs/image:dxdrawcircle.jpg.md "wikilink")

<table border=0>
<tr>
<td valign=top height=170>
[Download shader\_circle.zip](http://nightly.mtasa.com/files/shaders/shader_circle.zip)
This resource exports a 'dxDrawCircle' function for use in your own scripts.
Example resource calling dxDrawCircle function from shader\_circle: [circle\_example.zip](http://nightly.mtasa.com/files/shaders/circle_example.zip)

</td>
</tr>
</table>
