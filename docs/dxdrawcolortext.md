Draws a string of text colored with hex codes (in \#RRGGBB format) on the screen for one frame. In order for the text to stay visible continuously, you need to call this function with the same parameters on each frame update (see [onClientRender](/docs/onclientrender.md "wikilink")).

It works the same as [dxDrawText](/docs/dxdrawtext.md "wikilink"), except word-wrapping (not implemented yet).

Syntax
------

``` lua
void dxDrawColorText ( string text, int left, int top [, int right=left, int bottom=top, int color=white, 
                       float scale=1, mixed font="default", string alignX="left", string alignY="top", string clip="false" ] )
```

### Required Arguments

-   **text:** the text to draw
-   **left:** the absolute X coordinate of the top left corner of the text
-   **top:** the absolute Y coordinate of the top left corner of the text

### Optional Arguments

-   **right:** the absolute X coordinate of the right side of the text bounding box. Used for text aligning.
-   **bottom:** the absolute Y coordinate of the bottom side of the text bounding box. Used for text aligning.
-   **color:** the color of the text, a value produced by [tocolor](/docs/tocolor.md "wikilink"). **Note**: alpha value of this color will be used for the whole string.
-   **scale:** the size of the text.
-   **font:** Either a custom [DX font](/docs/dx_font.md "wikilink") element or the name of a built-in DX font:

-   **alignX:** horizontal alignment of the text within the bounding box. Can be **“left”**, **“center”** or **“right”**.
-   **alignY:** vertical alignment of the text within the bounding box. Can be **“top”**, **“center”** or **“bottom”**.
-   **clip:** if set to true, the parts of the text that don't fit within the bounding box will be cut off.

Code
----

<section name="Function source" class="both" show="true">
``` lua
function dxDrawColorText(str, ax, ay, bx, by, color, scale, font, alignX, alignY)
  bx, by, color, scale, font = bx or ax, by or ay, color or tocolor(255,255,255,255), scale or 1, font or "default"
  if alignX then
    if alignX == "center" then
      ax = ax + (bx - ax - dxGetTextWidth(str:gsub("#%x%x%x%x%x%x",""), scale, font))/2
    elseif alignX == "right" then
      ax = bx - dxGetTextWidth(str:gsub("#%x%x%x%x%x%x",""), scale, font)
    end
  end
  if alignY then
    if alignY == "center" then
      ay = ay + (by - ay - dxGetFontHeight(scale, font))/2
    elseif alignY == "bottom" then
      ay = by - dxGetFontHeight(scale, font)
    end
  end
   local clip = false
   if dxGetTextWidth(str:gsub("#%x%x%x%x%x%x","")) > bx then clip = true end
  local alpha = string.format("%08X", color):sub(1,2)
  local pat = "(.-)#(%x%x%x%x%x%x)"
  local s, e, cap, col = str:find(pat, 1)
  local last = 1
  local text = ""
  local broke = false
  while s do
    if cap == "" and col then color = tocolor(getColorFromString("#"..col..alpha)) end
    if s ~= 1 or cap ~= "" then
      local w = dxGetTextWidth(cap, scale, font)
           if clip then
                local text_ = ""
                 for i = 1,string.len(cap) do
                  if dxGetTextWidth(text,scale,font) < bx then
                  text = text..""..string.sub(cap,i,i)
                  text_ = text_..""..string.sub(cap,i,i)
                  else
                  broke = true
                   break
                  end
                 end
                 cap = text_
                end
      dxDrawText(cap, ax, ay, ax + w, by, color, scale, font)
      ax = ax + w
      color = tocolor(getColorFromString("#"..col..alpha))
    end
    last = e + 1
    s, e, cap, col = str:find(pat, last)
  end
  if last <= #str and not broke then
    cap = str:sub(last)
                   if clip then
                local text_ = ""
                 for i = 1,string.len(cap) do
                  if dxGetTextWidth(text,scale,font) < bx then
                  text = text..""..string.sub(cap,i,i)
                  text_ = text_..""..string.sub(cap,i,i)
                  else
                  broke = true
                   break
                  end
                 end
                 cap = text_
                end
    dxDrawText(cap, ax, ay, ax + dxGetTextWidth(cap, scale, font), by, color, scale, font)
  end
end
```

</section>
Author: Aibo Editor: MJNONFIK (add clip function)

See Also
--------
