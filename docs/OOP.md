Object Orientated Programming was introduced in MTA:SA 1.4 and comes with special utility classes like [Vector](/Vector.md "wikilink") and [Matrix](/Matrix.md "wikilink"). This page contains general information about the OOP functions and provides useful links.

Turning it on
-------------

By default, OOP is disabled (however, vectors and matrices are always available) - this is mainly because the vast majority of servers will prefer to stick to what they know - procedural programming. In fact, functions are still available even when OOP is enabled. Enabling OOP is as simple as adding the following line to the resource meta file:

``` xml
<oop>true</oop>
```

Vectors and Matrices
--------------------

[Vectors](/Vector.md "wikilink") and [Matrices](/Matrix.md "wikilink") make it easier to drop the complex maths and go straight ahead with fun part of maths. As mentioned above, OOP does not have to be enabled in the server config for this to be enabled.

Understanding the documentation
-------------------------------

The documentation for the OOP syntax intends to be very simplistic and is supported by the procedural syntax. To keep things simple, everything is consistently formatted in a certain way.

<section name="Example" class="generic" show="true">
</section>
-   Sometimes a note is added to the page. This will explain any special differences in the use of OOP for that function.
-   Methods can either start like *[player](/player.md "wikilink"):* or *[Player](/Player.md "wikilink").* - the former is only for a function on an instance (setPlayerHealth) and the latter is a static method (getRandomPlayer).
-   The counterpart section this allows you to see at a glance how the variable can be used. In most cases this can be inferred from the function page.

If you are a contributor to the wiki, please also consider reading [the OOP template](/Template:OOP.md "wikilink").

ADVANCED: OOP Metatable Structure
---------------------------------

You will understand this if you're proficient with Lua and have a decent understanding of metatables. Understanding this section is not necessary to use OOP.

``` lua
-- Exposed to global environment
Element = {
    create = createElement,
    setPosition = setElementPosition,
    ...
}

Vehicle = {
    create = createVehicle,
    setColor = setVehicleColor,
    ...
}

-- Hidden in lua registry, applied to userdata
ElementMT = {
    __index = CLuaClassDefs::Index,
    __newindex = CLuaClassDefs::NewIndex,
    __class = Element,
    __call = __class.create,
    __set = {
        type = CLuaClassDefs::ReadOnly,
        health = setElementHealth,
        ...
    },
    __get = {
        type = getElementType,
        health = getElementHealth,
        ...
    },
}

VehicleMT = {
    __index = CLuaClassDefs::Index,
    __newindex = CLuaClassDefs::NewIndex,
    __class = Vehicle,
    __parent = ElementMT,
    __call = __class.create,
    __set = {
        damageProof = setVehicleDamageProof
        ...
    },
    __get = {
        damageProof = isVehicleDamageProof
        ...
    },
}
```

Useful Links
------------

-   **[OOP Introduction](/OOP_Introduction.md "wikilink")** - teaches you about the basics of OOP
-   **[Function list (client)](/OOP_client.md "wikilink")** and **[Function list (server)](/OOP_server.md "wikilink")** - a list of functions implemented

[Category:OOP](/Category:OOP.md "wikilink")
