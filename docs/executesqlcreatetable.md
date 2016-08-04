This function creates a table in the database. It doesn't do anything when the table already exists. You can use this function in the loading or initialisation step of your script to ensure all the necessary tables that you use actually exist.

The executed SQL query is the following:

``` sql
CREATE TABLE IF NOT EXISTS <table> ( <definition> )
```

Syntax
------

``` lua
bool executeSQLCreateTable ( string tableName, string definition )
```

### Required Arguments

-   **tableName:** The name of the table you want to create.
-   **definition:** The definition of the table, this includes the column definitions and constraints in SQL syntax. For each column definition, you start with the name (without any spaces), optionally followed by the [SQL data type](http://www.sqlite.org/datatype3.html) and constraint (all separated by spaces). Each column definition is separated by a comma (,) (e.g. *field1,field2,field3* or *field1 INTEGER,field2 TEXT* as definition). Please refer to the [SQLite SQL documentation](http://www.sqlite.org/lang_createtable.html) for more information on creating even more complex tables.

### Returns

The function returns *true* on success, and *false* on failure.

Example
-------

This example creates a SQL table when the resource starts.

``` lua
function createSQLOnStart ()
    -- create our table, if it doesn't already exist
    executeSQLCreateTable ( "players", "clothes_head_texture TEXT, clothes_head_model TEXT, player TEXT" )
end
addEventHandler ( "onResourceStart", getResourceRootElement(),createSQLOnStart ) 
```

See Also
--------
