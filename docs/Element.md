An **element** is a generic class that can represent almost all in-game [entities](/entity.md "wikilink"). The built-in element types are:

Any other element type can be created as an abstract element, not referring to any game [entity](/entity.md "wikilink"). For example, **resource** and **map** elements are created when resources and maps are loaded to group entities they create as their children.

Elements share common functions such as type and list retrieval, a destroy operation to remove both the element and the game entity it is linked to (except for some elements which can't be destroyed, for example client elements), [element data](/element_data.md "wikilink") storing and retrieval, and many more common operations.

All elements are stored internally in a [tree structure](/Element_tree.md "wikilink"), and as such every element except the **root** element has a parent element, that can be the **root** element, a **resource**, **map** or another element. This is purely for declaring the scope of function calls.

Related scripting functions
---------------------------

### Client

### Server

[Category:Scripting Concepts](/Category:Scripting_Concepts.md "wikilink")

[it:Elemento](/it:Elemento.md "wikilink") [ru:Element](/ru:Element.md "wikilink") [es:Elemento](/es:Elemento.md "wikilink")
