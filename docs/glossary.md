## Glossary

##### Datastores

+ _Compare with [SQL](https://commons.wikimedia.org/wiki/File:SQL_ANATOMY_wiki.svg#/media/File:SQL_ANATOMY_wiki.svg)_
+ _Compare with [Mongo](https://docs.mongodb.org/manual/reference/glossary/#term-aggregation-framework)_

| Term         | Definition
| ------------ | --------------------------------------------------------
| record       | The basic unit of data in Waterline; a dictionary with multiple keys. Always contains a primary key field (e.g. `id: 7`).  Equivalent to a SQL row or a Mongo document.
| primary key  | A record's unique identifier. Always either an integer or a string.
| field        | A key/value pair stored as part of a record (e.g. `title:'Robinson Crusoe'`).  The key (left-hand side) is a column name and the value (right-hand side) is any value compatible with the database.
| primary key field  | The key/value pair stored as part of a record (e.g. `id:7`) which uniquely identifies it in the table.
| column name  | The name of a key which is present in all records in a particular table. Equivalent to a SQL column name.
| table        | A set of (at least partially) homogeneous records.  Equivalent to a SQL table or Mongo collection.
| datastore    | A set of tables. Equivalent to a SQL or Mongo "database".


##### Statements

+ _Compare with [SQL](https://commons.wikimedia.org/wiki/File:SQL_ANATOMY_wiki.svg#/media/File:SQL_ANATOMY_wiki.svg)_
+ _Compare with [Mongo](https://docs.mongodb.org/manual/reference/glossary/#term-aggregation-framework)_

| Term         | Definition
| ------------ | --------------------------------------------------------
| statement    | e.g. `{ select: ['title', 'author'], from: 'books', where: {title: 'robinson crusoe'} }`
| clause       | e.g. `from: 'books'` or `select: ['title', 'author']`.
| expression   | e.g. `title = 'robinson crusoe'`
