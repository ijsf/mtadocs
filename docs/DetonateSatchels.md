This function can be used to detonate a players satchels.

Syntax
------

<section name="Client" class="client" show="true">
``` lua
bool detonateSatchels ( )
```

</section>
<section name="Server" class="server" show="true">
``` lua
bool detonateSatchels ( player Player )
```

</section>
Returns
-------

Returns *true* if successful, *false* otherwise.

Example
-------

The below example allows a player to detonate any of their placed satchels via the command /blowsatchels

<section name="Client" class="client" show="true">
``` lua
function blowMySatchels()
    detonateSatchels()
    outputChatBox("Satchels blown!", 0, 255, 0)
end
addCommandHandler("blowsatchels", blowMySatchels)
```

</section>
See also
--------

[it:detonateSatchels](/it:detonateSatchels.md "wikilink") [pl:detonateSatchels](/pl:detonateSatchels.md "wikilink")
