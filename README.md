# Waterline Query Docs

> NOTE: This is for the next generation of Waterline Query Syntax and is not valid in the current version of Waterline.

This will document the declarative query syntax used in the Waterline Query Builder
notation. Through this syntax you should be able to compose complex queries that
can run on both a SQL data store or a NoSQL data store. The language is completely
database independent. This acts as an interchange format that can be processed
by an adapter and interpreted to be run on that particular database. It is highly
influenced by a relational sequel language but should be normalized enough to
be converted into NoSql queries as well.


### Table of Contents

* [Overview](docs/overview.md)
* [Finding Records](docs/read-operations.md)
* [Writing Records](docs/write-operations.md)
* [Aggregations](docs/aggregations.md)
* Extensions
  * [PostgreSQL Schema](docs/pg-schema.md)
* [Glossary](docs/glossary.md)
