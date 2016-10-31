## PostgreSQL Schema (Extension)

PostgreSQL supports the concept of a [**schema**](http://www.tutorialspoint.com/postgresql/postgresql_schema.htm) (in the sense of _a named collection of tables_). If you are using the PostgreSQL driver, you can specify a schema in your Waterline query using the `opts` key.

```javascript
{
  select: ['*'],
  from: 'user',
  opts: {
    schema: 'foo'
  }
}
```


Since individual queries can reach across multiple schemas in PostgreSQL, schemas may also be specified within subqueries.

```javascript
{
  select: ['*'],
  from: 'accounts',
  opts: {
    schema: 'foo'
  },
  where: {
    and: [
      {
        id: {
          in: {
            select: ['id'],
            from: 'users',
            opts: {
              schema: 'foo'
            },
            where: {
              or: [
                { status: 'active' },
                { name: 'John' }
              ]
            }
          }
        }
      }
    ]
  }
}
```
