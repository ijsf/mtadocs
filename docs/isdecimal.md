<lowercasetitle></lowercasetitle>

This function determines if number are decimal or not.

Syntax
------

``` lua
bool isDecimal( float number )
```

### Required Arguments

-   **number**: The number to compare.

### Returns

Return **false** if number not contain decimals or return **true** if number contain decimals

Code
----

<section name="Server- and/or clientside Script" class="both" show="true">
<code lang="lua"> function isDecimal(number) local \_number = tonumber(number) local x = math.abs(\_number) local y = math.abs(math.floor(\_number))

`   if (x - y) == 0 then`
`   return false`
`   else`
`   return true`
`   end`

end

</syntaxhighlight>
</section>
Author: VeNaD

See Also
--------
