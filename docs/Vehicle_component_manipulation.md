Vehicle component manipulation
------------------------------

With the introduction of vehicle component movement we now have the ability to manipulate parts of the model independently on a per vehicle basis which includes hiding parts, moving parts and rotating parts relative to the vehicle they are currently on.

The Abilities
-------------

Position: You can reposition a component relative to it's chassis or parent

Rotate: You can rotate the component around it's axis

Hide/Show: You can hide the component so it no longer shows or shows

How it works
------------

Adding components is very simple if you have any previous modelling experience each model part can have a name this name acts as a unique identifier for the part.

for ease of use it is possible to add hidden by default components by prefixing this name with a \# in the model file though it will not work on anything the game recognizes for instance wheels cannot be hidden by default so it might be best to prefix anything you wish to add.

like so: *\#*hellokitty

This can be re-shown any time and the shown flag is persistent across streaming unless you re-hide it after.

Any components need to be under the chassis dummy at least.

Simple things
-------------

The scripting functions make things like adding wheels very easy it should be fairly easy to add and spin wheels by copying the rotation from others into your wheel each frame and you can hide the originals using the hide function if need be.

This could be useful for an insane amount of wheels on a tank!

or just making more than 2 props work on planes

Generally speaking things that spin are fairly easy to do it's more complex animations that require the hardest work but eventually there should be an animation library on google code when it's finished to help with this.

An interesting idea
-------------------

It should be theoretically possible to add different types of doors to one model e.g. gull wings and scissor doors which could work like so:

Hide the original door

say the rotation of your normal door is between 0 and 45 degrees so you use that as a base for your movement

take that rotation and apply it on another axis for a different type of door or split it between axis each frame to get smooth door movement of the new door ( BONUS: it even works with swinging doors! )

James bond style
----------------

Guns, guns and ... rockets? are the order of the day secret panels with hidden rockets? no problem!

More advanced
-------------

There are no limits on the amount of moving, hidden or showing parts and anything hidden will not be rendered so you can add thousands of parts hidden and you should not have to worry about them slowing anything down.

This means that there is nothing stopping anyone from making a fully transforming transformer robot which changes from a car to a robot but this will require a lot of work on both the modelling and scripting side.

[Category:ID Lists](/Category:ID_Lists.md "wikilink")
