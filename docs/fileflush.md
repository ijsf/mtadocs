Forces pending disk writes to be executed. [fileWrite](/docs/filewrite.md "wikilink") doesn't directly write to the hard disk but places the data in a temporary buffer; only when there is enough data in the buffer it is actually written to disk. Call this function if you need the data written right now without closing the file. This is useful for log files that might want to be read while the resource is still executing. [fileFlush](/docs/fileflush.md "wikilink") can be called after each log entry is written. Without this, the file may appear empty or outdated to the user.

Syntax
------

``` lua
bool fileFlush ( file theFile )
```

### Required Arguments

-   **theFile:** The file handle of the file you wish to flush.

### Returns

Returns *true* if succeeded, *false* in case of failure (e.g. the file handle is invalid).

Example
-------

``` lua
local fileHandle = fileCreate("test.txt")
if fileHandle then
    fileWrite(fileHandle, "Line 1")
    fileFlush(fileHandle)
    -- ... further writing operations
    fileClose(fileHandle)
end
```

Note that [fileClose](/docs/fileclose.md "wikilink") automatically flushes the file.

See Also
--------
