This file holds all the MTA ChatBox Presets. Everything in this file deals with the chatbox and nothing else but the chatbox. This file is located with the [coreconfig.xml](/docs/coreconfig.xml.md "wikilink"). Its file path is *MTA San Andreas 1.x\\MTA*. You could even customize it yourself but you would need to be careful else MTA might crash or the chat might not even be visible. You can customize these in the Settings too.

### Children of the chatboxpresets

-   **preset name**: The name of the preset.
    -   **color\_text**: Text color (3 color values 'RGB' and optional transparent value) | example: 255 255 255 (White) or 255 255 255 122 (White and 47% transparent)
    -   **color\_background**: The background color (3 color values 'RGB' and 1 transparency value) | example: 255 0 0 122 (Fully red and 47% transparent)
    -   **color\_input\_text**: The color of the input text (3 color values 'RGB' and 1 transparency value)
    -   **color\_input\_background**: The color of the background while input is enabled (3 color values 'RGB' and 1 transparency value)
    -   **font**: The number of the font (0-3). | 0 - Tahoma, 1 - Verdana, 2 - Tahoma Bold, 3 - Arial
    -   **lines**: (Not-sure)
    -   **scale**: The scale of the text.
    -   **width**: The width of the text.
    -   **css\_text**: (Not sure what this is!)
    -   **css\_background**: (Not sure what this is!)
    -   **line\_life**: The amount of milliseconds for a line to be visible.
    -   **line\_fadeout**: The amount of milliseconds for a line to fade out.

### File Example

{{\#tag:code | <chatboxpresets>

`   `<preset name="MTA Blue (default)">
`       `<color_text>`255 255 255`</color_text>
`       `<color_background>`0 0 128 100`</color_background>
`       `<color_input_text>`172 213 254 255`</color_input_text>
`       `<color_input_background>`0 0 129 110`</color_input_background>
`       `<font>`0`</font>
`       `<lines>`7`</lines>
`       `<scale>`1 1`</scale>
`       `<width>`1`</width>
`       `<css_text>`0`</css_text>
`       `<css_background>`0`</css_background>
`       `<line_life>`12000`</line_life>
`       `<line_fadeout>`3000`</line_fadeout>
`   `</preset>
`   `<preset name="MTA Black">
`       `<color_text>`255 255 255`</color_text>
`       `<color_background>`0 0 0 100`</color_background>
`       `<color_input_text>`172 213 254 255`</color_input_text>
`       `<color_input_background>`0 0 0 110`</color_input_background>
`       `<font>`0`</font>
`       `<lines>`7`</lines>
`       `<scale>`1 1`</scale>
`       `<width>`1`</width>
`       `<css_text>`0`</css_text>
`       `<css_background>`0`</css_background>
`       `<line_life>`12000`</line_life>
`       `<line_fadeout>`3000`</line_fadeout>
`   `</preset>
`   `<preset name="Transparent">
`       `<color_text>`255 255 255`</color_text>
`       `<color_background>`0 0 0 0`</color_background>
`       `<color_input_text>`172 213 254 255`</color_input_text>
`       `<color_input_background>`0 0 0 0`</color_input_background>
`       `<font>`2`</font>
`       `<lines>`10`</lines>
`       `<scale>`1 1`</scale>
`       `<width>`1.5`</width>
`       `<css_text>`0`</css_text>
`       `<css_background>`0`</css_background>
`       `<line_life>`12000`</line_life>
`       `<line_fadeout>`3000`</line_fadeout>
`   `</preset>
`   `<preset name="Race Oversized">
`       `<color_text>`172 213 254 255`</color_text>
`       `<color_background>`0 0 128 100`</color_background>
`       `<color_input_text>`172 213 254 255`</color_input_text>
`       `<color_input_background>`0 0 191 110`</color_input_background>
`       `<font>`3`</font>
`       `<lines>`10`</lines>
`       `<scale>`1.65 1.17`</scale>
`       `<width>`1.2`</width>
`       `<css_text>`0`</css_text>
`       `<css_background>`0`</css_background>
`       `<line_life>`12000`</line_life>
`       `<line_fadeout>`3000`</line_fadeout>
`   `</preset>
`   `<preset name="iRace 2009">
`       `<color_text>`172 213 254 255`</color_text>
`       `<color_background>`0 0 128 0`</color_background>
`       `<color_input_text>`172 213 254 255`</color_input_text>
`       `<color_input_background>`0 0 191 110`</color_input_background>
`       `<font>`0`</font>
`       `<lines>`10`</lines>
`       `<scale>`1.5 1.1`</scale>
`       `<width>`1.2`</width>
`       `<css_text>`1`</css_text>
`       `<css_background>`0`</css_background>
`       `<line_life>`30000`</line_life>
`       `<line_fadeout>`300000`</line_fadeout>
`   `</preset>

</chatboxpresets> |lang=“xml”}}

[Category:Incomplete](/docs/Category:Incomplete.md "wikilink")
