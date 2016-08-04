This functions performs a bitwise circular right-rotation on the integer **value** by integer **n** positions. See [Bitwise operation](https://en.wikipedia.org/wiki/Bitwise_operation#Rotate_no_carry) for more details.

Syntax
------

``` lua
int bitRRotate ( int value, int n )
```

### Required arguments

-   **value:** The value you want to perform the rotation on.
-   **n:** The amount of positions to rotate the value by.

### Returns

Returns the circular right-rotated value as *integer*.

Example
-------

<section name="Client" class="client" show="true">
This example adds the clientside command **/rightrotate \[value\] \[positions = 1\]**, which will print the result from the function [bitRRotate](/docs/bitrrotate.md "wikilink").

``` lua
function getNumberAsBitString(value)
    if type(value) ~= 'number' then
        return false
    else
        local binary = ''

        for field = 31, 0, -1 do
            binary = binary .. bitExtract(value, field)

            if field % 4 == 0 then
                binary = binary ..' '
            end
        end

        return binary
    end
end

addCommandHandler('rightrotate',
    function (command, value, positions)
        if type(value) ~= 'string' or value:len() == 0 then
            return outputChatBox('* Syntax: /rightrotate [value] [positions = 1]')
        end

        if type(positions) ~= 'string' or positions:len() == 0 then
            positions = 1
        end

        local result = bitRRotate(tonumber(value), tonumber(positions))
        local binary = getNumberAsBitString(result)

        outputChatBox('* Decimal: '.. result ..', Binary: '.. binary)
    end
)
```

If you trigger the command with **/rightrotate 0xFF0000 16** you will receive as response:

    * Decimal: 255, Binary: 0000 0000 0000 0000 0000 0000 1111 1111 

</section>
See Also
--------
