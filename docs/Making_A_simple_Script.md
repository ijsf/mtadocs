**So We Are Gonna Make a script. Lets start And not waste time!! We are gonna make a GUI!! (Without Button Effects)**

Create a file named client.lua in folder Tutorial to start it.

1. Lets Write it what are we going to make:

`    window = {},`
`     label = {},`
`      memo = {}`
` }`

2. Now add lets add AddEventHandeler and the Function .

` addEventHandler(`“`onClientResourceStart`”`, resourceRoot,`
`     function()`

3. Lets Add window :

` guiCreateWindow(312, 331, 691, 481, `“`Name` `Of` `GUI`”`, false)`
`        guiSetProperty(GUI1, `“`CaptionColour`”`, `“`FF8E46B8`”`)`

4. Now We Will Add a image to it. Name the image mtaimage.jpg.

` function showClientImage()`
`  guiCreateStaticImage( 20, 200, 100, 100, `“`mtaimage.jpg`”`, false )`
` end`

5. Now We will add AddEventHandeler.

` addEventHandler( `“`onClientResourceStart`”`, getResourceRootElement( getThisResource() ), showClientImage )`

6. Lets add Memo to it.

` guiCreateMemo(80, 197, 573, 262, `“`Write` `Text` `here` `use` `/n` `for` `leaving` `a` `line.` `So` `see` `this` `example.`”`, false, GUI-Memu1)`

7. We Will Add Label To it now.

` guiCreateLabel(211, 44, 296, 143, `“`Text` `Here`”`, false, GUI-Label-1)`

8. We will add color's to Label.

` guiLabelSetColor(GUI-Label-1, 11, 22, 242)   `

9. Now Lets add end to it. Script will be over.

`end`

Whole Script :

`  window = {},`
`   label = {},`
`   memo = {}`
`]`
`addEventHandler(`“`onClientResourceStart`”`, resourceRoot,`
`    function()`
`guiCreateWindow(312, 331, 691, 481, `“`Name` `Of` `GUI`”`, false)`
`       guiSetProperty(GUI1, `“`CaptionColour`”`, `“`FF8E46B8`”`)`
`function showClientImage()`
` guiCreateStaticImage( 20, 200, 100, 100, `“`mtaimage.jpg`”`, false )`
`end`
` addEventHandler( `“`onClientResourceStart`”`, getResourceRootElement( getThisResource() ), showClientImage )`
`  guiCreateMemo(80, 197, 573, 262, `“`Write` `Text` `here` `use` `/n` `for` `leaving` `a` `line.` `So` `see` `this` `example.`”`, false, GUI-Memu1)`
`   guiCreateLabel(211, 44, 296, 143, `“`Text` `Here`”`, false, GUI-Label-1)`
`   guiLabelSetColor(GUI-Label-1, 11, 22, 242)   `
`end`

This Page is made by Anubhav! Contact him for Information or problems.
