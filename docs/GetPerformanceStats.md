This function returns performance information.

Syntax
------

``` lua
table table getPerformanceStats ( string category [, string options = "", string filter = "" ] )
```

### Required Arguments

-   **category:** Performance statistics category. If empty string is given, list of all categories is returned.

### Optional Arguments

-   **options:** Category specific ',' separated options. All categories supports 'h' option for help.
-   **filter:** Case-sensitive filter used to select returned rows. Only 'name' column is filtered.

### Returns

Returns two tables. First contains column names. The second contains result rows. Each row is table of cells.

Example
-------

``` lua
local columns, rows = getPerformanceStats("")
outputChatBox(table.concat(columns, "  "))
outputChatBox("----------------")
for i, row in ipairs(rows) do
  outputChatBox(table.concat(row, "  "))
end
```

See Also
--------
