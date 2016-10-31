## Overview

Waterline statements are self contained dictionaries that contain all the information needed to perform a query. They are database independent and can be run on either a SQL database such as MySQL or PostgreSQL or on a NoSQL database such as MongoDB.

#### Queries

A query targets a specific table of records which is equal to a database table in SQL or a collection in MongoDB. It may contain criteria that will identify which records from the table to return. It may also contain projections which specifies which fields from the table to return. You can also add clauses which modify the query to impose limits such as `skip`, `limit`, or `sort`.

In the following example you will see the various pieces that make up a Waterline read query. For more details see the [Read Operations](read-operations.md) docs.

```javascript
{
  // Operation clause with projections
  select: ['name', 'age'],
  from: 'user',
  // Criteria
  where: {
    and: [
      {
        age: {
          '>': 18
        }
      }
    ]
  },
  // Modifiers
  orderBy: [
    {
      age: 'desc'
    }
  ]
}
```

#### Data Modification

Queries may also create or modify records in a table. For `update` and `delete` operations a criteria may be specified that selects the records to perform the operation on.

In the following example you will see the various pieces that make up a Waterline write query. For more details see the [Write Operations](write-operations.md) docs.

```javascript
{
  // Data to be written
  update: {
    status: 'archived'
  },
  // Table to use
  using: 'books',
  // Criteria to filter the records by
  where: {
    and: [
      {
        publishedDate: {
          '>': 2000
        }
      }
    ]
  },
}
```
