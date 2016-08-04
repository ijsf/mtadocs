Syntax
------

``` lua
string teaDecode ( string data, string key )
```

### Required Arguments

-   **data:** The block of data you want to decrypt
-   **key:** The key that should be used for decryption (Only first 16 characters are used)

### Returns

Returns string containing the decrypted data if the decryption process was successfully completed, *false* otherwise.

Example
-------

<section name="Example 1" class="client" show="true">
This example creates a /teadecrypt command, which reverts the TEA on a given string with the specified key.

    [lua]
    function decryptString( cmd, theString, theKey )
        if ( theString ) and ( theKey ) then
            local decodedString = teaDecode( theString, theKey ) -- Decode the string with the key
            outputChatBox( "The decoded string is: " .. tostring( decodedString ) )
        else
            outputChatBox( "Syntax: /" .. cmd .. " [string] [key]" )
        end
    end
    addCommandHandler( "teadecrypt", decryptString )

</section>
See Also
--------
