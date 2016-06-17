## Criteria

Criteria is used to filter the records that will be returned from a query. It is always specified using the `where` key in the query. The following examples explain the various `operators` and `conditions` that can be applied inside the criteria dictionary.

#### Equality

To specify an equality condition use a key/value pair where the key represents a column name and the value represents the expected record value. The following example returns records from the inventory table where the **type** is equal to **snack**.

```javascript
{
  select: ['*'],
  from: 'inventory',
  where: {
    type: 'snack'
  }
}
```

#### Operators

A query may also specify a comparison operator to be used. Operators are specified as a key inside a dictionary. The following operators are supported:

* Greater Than `>` selects records whose field is greater than the specified value.

```javascript
{
  select: ['*'],
  from: 'users',
  where: {
    age: {
      '>': 20
    }
  }
}
```

* Greater Than Or Equal `>=` selects records whose field is greater than or equal to the specified value.

```javascript
{
  select: ['*'],
  from: 'users',
  where: {
    age: {
      '>=': 20
    }
  }
}
```

* Less Than `<` selects records whose field is less than the specified value.

```javascript
{
  select: ['*'],
  from: 'users',
  where: {
    age: {
      '<': 20
    }
  }
}
```

* Less Than Or Equal `>=` selects records whose field is less than or equal to the specified value.

```javascript
{
  select: ['*'],
  from: 'users',
  where: {
    age: {
      '<=': 20
    }
  }
}
```

* IN `in` selects records where the value of the field equals any of the values in the list.

```javascript
{
  select: ['*'],
  from: 'users',
  where: {
    shoeSize: {
      in: [8,9,10]
    }
  }
}
```

> To filter by range and, more generally, to combine multiple operators (e.g. `>`/`<`/`in`/etc), use `and` (described below).




#### Conditions

A condition is used to either combine multiple criteria clauses or to negate an operator or a set of operators. The following conditions are supported:

* `AND` is implicitly set when you define multiple conditions. It is used to connect multiple clauses together so that the query selects records that match all of the conditions specified.

```javascript
{
  select: ['*'],
  from: 'users',
  where: {
    firstName: 'John',
    lastName: 'Smith'
  }
}
```

* `OR` conditions are used to specify that a record must match at least one of the conditions in the list.

The following query selects all users whose firstName is John **OR** whose lastName is Smith.

```javascript
{
  select: ['*'],
  from: 'users',
  where: {
    or: [
      {
        firstName: 'John'
      },
      {
        lastName: 'Smith'
      }
    ]
  }
}
```

You can mix both `AND` and `OR` statements together to form complex where clauses. The following example finds all records whose type is equal to **food** and either the **qty** is `>` **100** or the **price** is `<` **10.00**.

```javascript
{
  select: ['*'],
  from: 'inventory',
  where: {
    type: 'food',
    or: [
      {
        qty: {
          '>': 100
        }
      },
      {
        price: {
          '<': 10.00
        }
      }
    ]
  }
}
```

`AND` may also be represented as an array if needed. This allows you to combine `OR` expressions.

```javascript
{
  select: ['*'],
  from: 'users',
  where: {
    and: [
      {
        or: [
          {
            firstName: 'John'
          },
          {
            lastName: 'Smith'
          }
        ]
      },
      {
        or: [
          {
            qty: {
              '>': 100
            }
          },
          {
            price: {
              '<': 10.00
            }
          }
        ]
      }
    ]
  }
}
```

* It also allows you to combine multiple sub-attribute modifiers:

```javascript
{
  select: ['*'],
  from: 'users',
  where: {
    and: [
      {
        age: { '>': 64 }
      },
      {
        age: { '<=': 101 }
      },
      {
        age: { '>': 64 }
      }
    ]
  }
}
```



* `NOT` can be used to negate a condition.

```javascript
{
  select: ['*'],
  from: 'inventory',
  where: {
    not: {
      type: 'food'
    }
  }
}
```

```javascript
{
  select: ['*'],
  from: 'inventory',
  where: {
    not: {
      shoeSize: {
        in: [8,9,10]
      }
    }
  }
}
```
