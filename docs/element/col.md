The [COL](/docs/col.md "wikilink") class represents a RenderWare Collision File (.col) loaded by the client, which can be imported into a custom model to define its collisions.

A .col file can contain one or more collision models. Normally, San Andreas assigns each collision model in a file to a geometry model through the model name that is embedded in the collision model. However in MTA, you can assign any .col file to any model ID; the names are ignored. To prevent loading multiple collision models into one model ID, MTA only loads the first collision model of a .col file and ignores the rest. Therefore, if you have a .col file containing multiple collision models, you will need to split it into multiple files, with one model per file, and then load and import each of those files using the appropriate scripting functions. To split a .col file into multiple files, you can use [CollEditor2](http://www.steve-m.com/downloads/tools/colleditor2/).

Collision data can also be embedded in DFF files. At the moment, vehicle collision replacement works with DFF embedded collisions only.

Related scripting functions
---------------------------

### Client
