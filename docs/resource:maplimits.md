Map Limits is a resource that allows defining points in a .map file to border a map. A player outside the border area will lose health until he dies or returns to the game area.

Usage
-----

Syntax:

``` lua
<maplimit>
    <point x="" y="" />
    <point x="" y="" />
    <point x="" y="" />
</maplimit>
```

When using maplimits in ones map, at least three points must be made.
Note that the sequence of points <b>matters</b>. Start in the bottom left corner and work counter-clockwise.

For example, this would create a square shaped border:

``` lua
<point x="0" y="0" />
<point x="1" y="0" />
<point x="1" y="1" />
<point x="0" y="1" />
```

While this would create two triangles:

``` lua
<point x="0" y="0" />
<point x="1" y="1" />
<point x="0" y="1" />
<point x="1" y="0" />
```

[ru:<Resource:Maplimits>](/docs/ru:resource:maplimits.md "wikilink")
