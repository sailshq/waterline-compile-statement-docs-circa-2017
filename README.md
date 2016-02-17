# Waterline Query Docs

This will document the declarative query syntax used in the Waterline Query Builder
notation. Through this syntax you should be able to compose complex queries that
can run on both a SQL data store or a NoSQL data store. The language is completely
database independent. This acts as an interchange format that can be processed
by an adapter and interpreted to be run on that particular database. It is highly
influenced by a relational sequel language but should be normalized enough to
be converted into NoSql queries as well.

For familiarity the generated SQL query is shown next to each example using the
PostgreSQL dialect. The equivalent MongoDB query is also shown.


### Table of Contents
