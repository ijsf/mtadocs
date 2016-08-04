This function copies a file.

Syntax
------

``` lua
bool fileCopy ( string filePath, string copyToFilePath [, bool overwrite = false ] )
```

### Required Arguments

-   **filePath**: The path of the file you want to copy.
-   **copyToFilePath**: Where to copy the specified file to.

### Optional Arguments

-   **overwrite**: If set to true it will overwrite a file that already exists at copyToFilePath.

Returns
-------

Return true if the file was copied, else false if the 'filePath' doesn't exist.

Example
-------

<section name="Server" class="server" show="true">
This example copies a file called 'test.txt' and called it 'test1.txt'.

``` lua
addEventHandler("onResourceStart", resourceRoot, function(res)
    local filePath = ":"..getResourceName(res).."/test.txt"
    fileCreate(filePath) --create the file in this resource and name it 'test.txt'.
    if fileCopy(filePath, ":"..getResourceName(res).."/test1.txt") then
         outputChatBox("File was successfully copied!", root, 0, 100, 0)
    else
         outputChatBox("File was not successfully copied, probably because it doesn't exist.", root, 100, 0, 0)
    end
end)
```

</section>
<section name="Client" class="client" show="true">
This example copies a file called 'test.txt' and called it 'test1.txt'.

``` lua
addEventHandler("onClientResourceStart", resourceRoot, function(res)
    local filePath = ":"..getResourceName(res).."/test.txt"
    fileCreate(filePath) --create the file in this resource and name it 'test.txt'.
    if fileCopy(filePath,":"..getResourceName(res).."/test1.txt") then
         outputChatBox("File was successfully copied!", 0, 100, 0)
    else
        outputChatBox("File was not successfully copied, probably because it doesn't exist.", 100, 0, 0)
    end
end)
```

</section>
See Also
--------
