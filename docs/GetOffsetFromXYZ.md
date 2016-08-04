<lowercasetitle></lowercasetitle>

This function can be used to get the relative x,y,z positions from an element and a world position. Requires the [Lua matrix library](/Lua_matrix_library.md "wikilink").

Syntax
------

``` lua
table getOffsetFromXYZ( mat, vector )
```

### Arguments

-   **mat**: a Matrix from the source vehicle
-   **vector**: an x,y,z position

### Returns

Returns a table containing the relative x, y, z positions.

Code
----

<section name="Server- and/or clientside Script" class="both" show="true">
<code lang="lua"> function getOffsetFromXYZ( mat, vec )

`   -- make sure our matrix is setup correctly 'cos MTA used to set all of these to 1.`
`   mat[1][4] = 0`
`   mat[2][4] = 0`
`   mat[3][4] = 0`
`   mat[4][4] = 1`
`   mat = matrix.invert( mat )`
`   local offX = vec[1] * mat[1][1] + vec[2] * mat[2][1] + vec[3] * mat[3][1] + mat[4][1]`
`   local offY = vec[1] * mat[1][2] + vec[2] * mat[2][2] + vec[3] * mat[3][2] + mat[4][2]`
`   local offZ = vec[1] * mat[1][3] + vec[2] * mat[2][3] + vec[3] * mat[3][3] + mat[4][3]`
`   return {offX, offY, offZ}`

end

</syntaxhighlight>
</section>
Example
-------

<section name="Client" class="client" show="true">
TODO <code lang="lua"> --todo

</syntaxhighlight>
</section>
See Also
--------
