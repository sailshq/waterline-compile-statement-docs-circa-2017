## Joins (Extension)

> NOTE: placeholder

SQL joins are supported in all SQL drivers using the sql generator. They are **NOT** available in any NoSQL drivers.

Joins are specified as an array of join conditions. Each condition is represented as a dictionary of values where the `from` key represents the child table being joined and the `on` key represents the logic for performing the join. The `on` key should be a dictionary with two keys, each one representing a table and the value representing a column name on the table that will act as a foreign key.

#### Join

```javascript
{
  select: ['users.id', 'contacts.phone'],
  from: 'users',
  join: [
    {
      from: 'contacts',
      on: {
        users: 'id',
        contacts: 'user_id'
      }
    }
  ]
}
```

#### Inner Joins

```javascript
{
  select: ['*'],
  from: 'users',
  innerJoin: [
    {
      from: 'accounts',
      on: {
        users: 'id',
        accounts: 'user_id'
      }
    }
  ]
}
```

#### Left Joins

```javascript
{
  select: ['*'],
  from: 'users',
  leftJoin: [
    {
      from: 'accounts',
      on: {
        users: 'id',
        accounts: 'user_id'
      }
    }
  ]
}
```

#### Left Outer Joins

```javascript
{
  select: ['*'],
  from: 'users',
  leftOuterJoin: [
    {
      from: 'accounts',
      on: {
        users: 'id',
        accounts: 'user_id'
      }
    }
  ]
}
```

#### Right Joins

**Example:**

```javascript
{
  select: ['*'],
  from: 'users',
  rightJoin: [
    {
      from: 'accounts',
      on: {
        users: 'id',
        accounts: 'user_id'
      }
    }
  ]
}
```

#### Right Outer Joins

```javascript
{
  select: ['*'],
  from: 'users',
  rightOuterJoin: [
    {
      from: 'accounts',
      on: {
        users: 'id',
        accounts: 'user_id'
      }
    }
  ]
}
```

#### Outer Joins

```javascript
{
  select: ['*'],
  from: 'users',
  outerJoin: [
    {
      from: 'accounts',
      on: {
        users: 'id',
        accounts: 'user_id'
      }
    }
  ]
}
```

#### Full Outer Joins

```javascript
{
  select: ['*'],
  from: 'users',
  fullOuterJoin: [
    {
      from: 'accounts',
      on: {
        users: 'id',
        accounts: 'user_id'
      }
    }
  ]
}
```

#### Cross Joins

```javascript
{
  select: ['*'],
  from: 'users',
  crossJoin: [
    {
      from: 'accounts',
      on: {
        users: 'id',
        accounts: 'user_id'
      }
    }
  ]
}
```
