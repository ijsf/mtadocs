Easing functions describe functions that control the way an interpolation between 0 and 1 is done.

The most basic easing function, linear, is just a linear interpolation at constant speed. Other more advanced easing functions can have acceleration at the beginning, the end or both or deceleration, or even bouncing or elastic effects.

Preliminary note
================

In the functions using easing, there are usually 3 optional parameters. Most functions don't need them at all, the ones needing one or more parameters are listed in the table below. When providing optional parameters, all the parameters before a given parameter must be filled, even if the easing function you intend to use doesn't require such a parameter. In this case, simply use 0 for the parameters you don't need. Examples:

-   *“Linear”* can be used simply with *getEasingValue( fProgress, “Linear” )*
-   *“OutElastic”* can define *fEasingPeriod* and *fEasingAmplitude* so it can be used with *getEasingValue( fProgress, “OutElastic”, 0.3, 1.0 )*
-   *“InBack”* can define *fEasingOvershoot*, but since it comes after *fEasingPeriod* and *fEasingAmplitude* in the order of parameters, 0 must be used for the others with *getEasingValue( fProgress, “InBack”, 0, 0, 1.7015 )*

Easing functions
================

``` lua
--List of builtin easing functions
builtins={ "Linear", "InQuad", "OutQuad", "InOutQuad", "OutInQuad", "InElastic", "OutElastic", "InOutElastic", "OutInElastic", "InBack", "OutBack", "InOutBack", "OutInBack", "InBounce", "OutBounce", "InOutBounce", "OutInBounce", "SineCurve", "CosineCurve" }
```

Default values are (when a function can use a parameter but it's not defined by the user):

-   *fEasingPeriod:* 0.3
-   *fEasingAmplitude :* 1.0
-   *fEasingOvershoot:* 1.701

<table border="1" class="unnamed1">
<tr>
<th align="center">
Easing function

</th>
<th align="center">
Function profile

</th>
<th align="center">
Uses fEasingPeriod

</th>
<th align="center">
Uses fEasingAmplitude

</th>
<th align="center">
Uses fEasingOvershoot

</th>
<th>
Comments

</th>
</tr>
<tr>
<td align="center">
Linear

</td>
<td align="center">
[<File:Qeasingcurve-linear.png>](/docs/file-qeasingcurve-linear.png.md "wikilink")

</td>
<td align="center">
</td>
<td align="center">
</td>
<td align="center">
</td>
<td>
</td>
</tr>
<tr>
<td align="center">
InQuad

</td>
<td align="center">
[<File:Qeasingcurve-inquad.png>](/docs/file-qeasingcurve-inquad.png.md "wikilink")

</td>
<td align="center">
</td>
<td align="center">
</td>
<td align="center">
</td>
<td>
</td>
</tr>
<tr>
<td align="center">
OutQuad

</td>
<td align="center">
[<File:Qeasingcurve-outquad.png>](/docs/file-qeasingcurve-outquad.png.md "wikilink")

</td>
<td align="center">
</td>
<td align="center">
</td>
<td align="center">
</td>
<td>
</td>
</tr>
<tr>
<td align="center">
InOutQuad

</td>
<td align="center">
[<File:Qeasingcurve-inoutquad.png>](/docs/file-qeasingcurve-inoutquad.png.md "wikilink")

</td>
<td align="center">
</td>
<td align="center">
</td>
<td align="center">
</td>
<td>
</td>
</tr>
<tr>
<td align="center">
OutInQuad

</td>
<td align="center">
[<File:Qeasingcurve-outinquad.png>](/docs/file-qeasingcurve-outinquad.png.md "wikilink")

</td>
<td align="center">
</td>
<td align="center">
</td>
<td align="center">
</td>
<td>
</td>
</tr>
<tr>
<td align="center">
InElastic

</td>
<td align="center">
[<File:Qeasingcurve-inelastic.png>](/docs/file-qeasingcurve-inelastic.png.md "wikilink")

</td>
<td align="center">
yes

</td>
<td align="center">
yes

</td>
<td align="center">
</td>
<td>
Due to the elastic effect, this easing function produces some values &lt; 0

</td>
</tr>
<tr>
<td align="center">
OutElastic

</td>
<td align="center">
[<File:Qeasingcurve-outelastic.png>](/docs/file-qeasingcurve-outelastic.png.md "wikilink")

</td>
<td align="center">
yes

</td>
<td align="center">
yes

</td>
<td align="center">
</td>
<td>
Due to the elastic effect, this easing function produces some values &gt; 1

</td>
</tr>
<tr>
<td align="center">
InOutElastic

</td>
<td align="center">
[<File:Qeasingcurve-inoutelastic.png>](/docs/file-qeasingcurve-inoutelastic.png.md "wikilink")

</td>
<td align="center">
yes

</td>
<td align="center">
yes

</td>
<td align="center">
</td>
<td>
Due to the elastic effect, this easing function produces some values &lt; 0 and &gt; 1

</td>
</tr>
<tr>
<td align="center">
OutInElastic

</td>
<td align="center">
[<File:Qeasingcurve-outinelastic.png>](/docs/file-qeasingcurve-outinelastic.png.md "wikilink")

</td>
<td align="center">
yes

</td>
<td align="center">
yes

</td>
<td align="center">
</td>
<td>
Due to the elastic effect, this easing function produces some values &lt; 0 and &gt; 1

</td>
</tr>
<tr>
<td align="center">
InBack

</td>
<td align="center">
[<File:Qeasingcurve-inback.png>](/docs/file-qeasingcurve-inback.png.md "wikilink")

</td>
<td align="center">
</td>
<td align="center">
</td>
<td align="center">
yes

</td>
<td>
Due to overshoot, this easing function produces some values &lt; 0

</td>
</tr>
<tr>
<td align="center">
OutBack

</td>
<td align="center">
[<File:Qeasingcurve-outback.png>](/docs/file-qeasingcurve-outback.png.md "wikilink")

</td>
<td align="center">
</td>
<td align="center">
</td>
<td align="center">
yes

</td>
<td>
Due to overshoot, this easing function produces some values &gt; 1

</td>
</tr>
<tr>
<td align="center">
InOutBack

</td>
<td align="center">
[<File:Qeasingcurve-inoutback.png>](/docs/file-qeasingcurve-inoutback.png.md "wikilink")

</td>
<td align="center">
</td>
<td align="center">
</td>
<td align="center">
yes

</td>
<td>
Due to overshoot, this easing function produces some values &lt;0 and &gt; 1

</td>
</tr>
<tr>
<td align="center">
OutInBack

</td>
<td align="center">
[<File:Qeasingcurve-outinback.png>](/docs/file-qeasingcurve-outinback.png.md "wikilink")

</td>
<td align="center">
</td>
<td align="center">
</td>
<td align="center">
yes

</td>
<td>
</td>
</tr>
<tr>
<td align="center">
InBounce

</td>
<td align="center">
[<File:Qeasingcurve-inbounce.png>](/docs/file-qeasingcurve-inbounce.png.md "wikilink")

</td>
<td align="center">
</td>
<td align="center">
yes

</td>
<td align="center">
</td>
<td>
</td>
</tr>
<tr>
<td align="center">
OutBounce

</td>
<td align="center">
[<File:Qeasingcurve-outbounce.png>](/docs/file-qeasingcurve-outbounce.png.md "wikilink")

</td>
<td align="center">
</td>
<td align="center">
yes

</td>
<td align="center">
</td>
<td>
</td>
</tr>
<tr>
<td align="center">
InOutBounce

</td>
<td align="center">
[<File:Qeasingcurve-inoutbounce.png>](/docs/file-qeasingcurve-inoutbounce.png.md "wikilink")

</td>
<td align="center">
</td>
<td align="center">
yes

</td>
<td align="center">
</td>
<td>
</td>
</tr>
<tr>
<td align="center">
OutInBounce

</td>
<td align="center">
[<File:Qeasingcurve-outinbounce.png>](/docs/file-qeasingcurve-outinbounce.png.md "wikilink")

</td>
<td align="center">
</td>
<td align="center">
yes

</td>
<td align="center">
</td>
<td>
</td>
</tr>
<tr>
<td align="center">
SineCurve

</td>
<td align="center">
[<File:Qeasingcurve-sincurve.png>](/docs/file-qeasingcurve-sincurve.png.md "wikilink")

</td>
<td align="center">
</td>
<td align="center">
</td>
<td align="center">
</td>
<td>
This easing function doesn't end at 1 but goes back to 0. In this case, for interpolation, the target value is just an edge but doesn't represent the stop value.

</td>
</tr>
<tr>
<td align="center">
CosineCurve

</td>
<td align="center">
[<File:Qeasingcurve-coscurve.png>](/docs/file-qeasingcurve-coscurve.png.md "wikilink")

</td>
<td align="center">
</td>
<td align="center">
</td>
<td align="center">
</td>
<td>
This easing function both starts and stops at 0.5, going first to 1 then 0. In this case, for interpolation, the source and target values are just the edges but don't represent the start/stop values.

</td>
</tr>
</table>
Examples
--------

<section show="true">
**Example 1:** This example move gate with easing.

``` lua
local x,y,z = 2096.3, 1721, 12.7
local easing = "OutBounce"
local time = 2000
local gate = createObject(980, x,y,z, 0, 0, 63)
local marker = createMarker(x,y,z, "cylinder", 12, 0, 0, 0, 0)
 
function moveGate(hitPlayer, matchingDimension)
        moveObject(gate, time, x+4.9, y+9.6, z, 0, 0, 0, easing)
end
addEventHandler("onMarkerHit", marker, moveGate)
 
function moveBack()
    moveObject(gate, time, x, y, z, 0, 0, 0, easing)
end
addEventHandler("onMarkerLeave", marker, moveBack)
```

</section>
Source
======

The naming conventions of the functions below, available in [moveObject](/docs/moveobject.md "wikilink"), [interpolateBetween](/docs/interpolatebetween.md "wikilink"), or [getEasingValue](/docs/geteasingvalue.md "wikilink") have been extracted from [Qt documentation](http://doc.qt.nokia.com/latest/qeasingcurve.html). Only a subset of those functions is available in MTA since some of them are a bit redundant (only the profile of the acceleration/deceleration changes). The pictures of the easing functions are directly extracted from Qt documentation, © 2008-2010 Nokia Corporation and/or its subsidiaries.
