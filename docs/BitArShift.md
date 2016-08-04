This functions performs an arithmetic shift on the integer **value** by integer **n** positions. In an *arithmetic shift*, zeros are shifted in to replace the discarded bits. In a *right arithmetic* shift, the [sign bit](https://en.wikipedia.org/wiki/Sign_bit) is shifted in on the left, thus preserving the sign of the operand. See [Bitwise operation](https://en.wikipedia.org/wiki/Bitwise_operation#Arithmetic_shift) for more details.

Syntax
------

``` lua
int bitArShift ( int value, int n )
```

### Required arguments

-   **value:** The value you want to perform the arithmetic shift on.
-   **n:** The amount of positions to shift the value by.

### Returns

Returns the arithmetic shifted value as *integer*.

Example
-------

<section name="Client" class="client" show="true">
This example adds the clientside command **/arshift \[value\] \[positions = 1\]**, which will print the result from the function [bitArShift](/bitArShift.md "wikilink").

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

addCommandHandler('arshift',
    function (command, value, positions)
        if type(value) ~= 'string' or value:len() == 0 then
            return outputChatBox('* Syntax: /arshift [value] [positions = 1]')
        end

        if type(positions) ~= 'string' or positions:len() == 0 then
            positions = 1
        end

        local result = bitArShift(tonumber(value), tonumber(positions))
        local binary = getNumberAsBitString(result)

        outputChatBox('* Decimal: '.. result ..', Binary: '.. binary)
    end
)
```

If you trigger the command with **/arshift 0xF0 4** and **/arshift 0xF0 -4** you will receive as response:

    * Decimal: 15,   Binary: 0000 0000 0000 0000 0000 0000 0000 1111
    * Decimal: 3840, Binary: 0000 0000 0000 0000 0000 1111 0000 0000

</section>
See Also
--------
