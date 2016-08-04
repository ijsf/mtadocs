A *boolean* or *bool* is a datatype whose value can be either *true* or *false*. These are often returned by functions to indicate whether the operation was successful or not.

Using the lua functions tostring() and type() can help you to find out what datatype something is:

    local theReturn = isPedDead(getRandomPlayer())
    outputChatBox("The return was: "..tostring(theReturn)) -- Will say: "true" or "false"
    outputChatBox("The datatype of this return was: "..type(theReturn)) -- Will say "boolean"

Reversing bools
---------------

    bool = true
    -- if you want to reverse it you can either do
    bool = false
    -- or
    bool = not bool

[Category:Scripting Concepts](/docs/category:scripting_concepts.md "wikilink")

[ru:Boolean](/docs/ru:boolean.md "wikilink") [de:Boolean](/docs/de:boolean.md "wikilink")
