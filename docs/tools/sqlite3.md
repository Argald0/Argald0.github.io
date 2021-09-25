# SQLite3

On smaller sites, it is quite common to see the database stored in a file; it is called a "**flat-file**" **database**.

## Extract information

In order to read into those databases, we use SQLite3 as follow :

1. Launch SQLite3 : `$ sqlite3 <database-name>`
2. Check the available tables : `sqlite> .tables`
3. Get more information about the table you are interested in : `sqlite> PRAGMA table_info(<table-name>);`
4. Query the table using SQL commands : `sqlite> select * from <table-name>;`