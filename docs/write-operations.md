## Write Operations

A write operation is anything that creates or modifies data. There are three types of `write` operations: `insert`, `update`, and `delete`.

An insert operation adds new records to a table. Update operations modify one or more existing records. Delete operations remove one or more records from the table.

For update and delete operations you may specify criteria for the operation to limit the records the operation is applied to.

#### Insert

An `insert` operation is defined using the `insert` key and the `into` key. Insert represents the data that will make up the new record and `into` represents the table that will be used for the insert.

```javascript
{
  // Values for the new record
  insert: {
    title: 'Slaughterhouse Five'
  },
  // Table to use
  into: 'books'
}
```

#### Update

An `update` operation is defined using the `update` key and the `using` key. Update represents the values that will be set on any records matching the criteria and `using` represents the table that will be used for the update.

```javascript
{
  // Values to set
  update: {
    status: 'archived'
  },
  // Criteria to use
  where: {
    and: [
      {
        publishedDate: { '>': 2000 }
      }
    ]
  },
  // Table to use
  using: 'books'
}
```

#### Delete

A `delete` operation is defined using the `del` key as `delete` is a reserved word in javascript.

**Example:**

```javascript
{
  // Del to show this will be a delete operation
  del: true,
  // The table to use
  from: 'accounts',
  // Criteria to use
  where: {
    and: [
      {
        activated: false
      }
    ]
  }
}
```
