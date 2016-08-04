This function frees a database query handle. dbFree only needs to be used if a result has not been obtained with [dbPoll](/docs/dbpoll.md "wikilink")

Syntax
------

``` lua
bool dbFree ( handle queryHandle )
```

### Required Arguments

-   **queryHandle:** A query handle previously returned from [dbQuery](/docs/dbquery.md "wikilink")

### Returns

Returns *true* if the handle was successfully freed, *false* otherwise.

Example
-------

##### These examples show when dbFree should be used:

<div style="margin-left:20px">
Required because [dbPoll](/docs/dbpoll.md "wikilink") was not called:

``` lua
local qh = dbQuery( connection, "SELECT * FROM table_name" )
dbFree ( qh )
```

Required because [dbPoll](/docs/dbpoll.md "wikilink") was not called:

``` lua
function aaa()
    dbQuery( myCallback, connection, "SELECT * FROM table_name" )
end

function myCallback(qh)
    dbFree ( qh )
end
```

Required because [dbPoll](/docs/dbpoll.md "wikilink") is called, but the result was not ready and no more attempts will be made:

``` lua
local qh = dbQuery( connection, "SELECT * FROM table_name" )
local result = dbPoll( qh, 10 )     -- Get result with a timeout of 10ms
if result == nil then
    result = dbPoll( qh, 10 )       -- Try again to get result with a timeout of 10ms
    if result == nil then
        dbFree( qh )                -- Give up
    end
end
```

</div>
=====These examples show when dbFree should NOT be used:=====

<div style="margin-left:20px">
Not required because [dbPoll](/docs/dbpoll.md "wikilink") was called with a -1 timeout:

``` lua
local qh = dbQuery( connection, "SELECT * FROM table_name" )
local result = dbPoll( qh, -1 )    -- Wait until result has been gotten
```

Not required because [dbPoll](/docs/dbpoll.md "wikilink") was called from the callback:

``` lua
function aaa()
    dbQuery( myCallback, connection, "SELECT * FROM table_name" )
end

function myCallback(qh)
    local result = dbPoll( qh, 0 )  -- Timeout doesn't matter here because the result will always be ready
end
```

</div>
Requirements
------------

See Also
--------
