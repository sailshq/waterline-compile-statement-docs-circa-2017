## Sub Queries (Extension)

> NOTE: placeholder

Sub Queries are supported in all SQL drivers using the sql generator. They are **NOT** available in any NoSQL drivers.

Sub Queries follow the same logic as a single level query. There are three types of valid subqueries: `predicate`, `scalar`, and `table`.

#### Predicate Subqueries

Predicate subqueries are valid when used inside a `where` clause to return a
list of values.

```javascript
{
  select: ['*'],
  from: 'accounts',
  where: {
    and: [
      {
        id: {
          in: {
            select: ['id'],
            from: 'users',
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

#### Scalar Subqueries

Scalar subqueries are valid when used as a single value. The subquery can only
return one column value.

```javascript
{
  select: ['name', {
    select: ['username'],
    from: 'users',
    where: {
      or: [
        { status: 'active' },
        { name: 'John' }
      ]
    },
    as: 'username'
  }, 'age'],
  from: 'accounts'
}
```

#### Table Subqueries

Table subqueries are valid when used as a single value in the `FROM` clause.
The subquery can only return one column value.

```javascript
{
  select: ['name', 'age'],
  from: {
    select: ['age'],
    from: 'users',
    where: {
      and: [
        {
          age: 21
        }
      ]
    }
  }
}
```
