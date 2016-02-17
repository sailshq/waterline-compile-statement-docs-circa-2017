## Read Operations

Read operations retrieve records from a table. It may contain criteria that identifies which records from the table to return along with projections that limit which fields from the table to return.

In Waterline all read operations are defined using the `select` key in the query. This tells Waterline that you would like to return data, it also can be used for projections. To find all fields you supply the value `select: ['*']` and to limit the fields returned you supply a list of field names `select: ['name', 'age']`. The next step is to provide a `table` to be used for the query. This is always represented as a single string value in the form `from: 'users'`. This is the minimum needed to create a valid read operation. From here you can add criteria and modifiers to limit the data returned.

```javascript
{
  // Select projections
  select: ['*'],
  // Table name
  from: 'users',
  // Criteria
  where: {
    name: 'bob'
  },
  // Modifiers
  limit: 10
}
```

#### Projections

Projections limit the fields returned from the query. It is always defined using the `select` key and is always represented by an array of values. The values correspond to the column name in the table. A helper is defined for returning all columns using the `*` value.

```javascript
{
  // Return all field values
  select: ['*'],
  // Table name
  from: 'users'
}
```

```javascript
{
  // Return only `id`, `name` and `age` field values
  select: ['id', 'name', 'age'],
  // Table name
  from: 'users'
}
```

#### Criteria

Criteria is always defined using the `where` key in the query. It's represented by a dictionary of values that define how the records should be filtered. It may contain `operators` and `conditions` as well as nested `sub queries` where supported.

See the [Criteria](criteria.md) docs for a full list of available options.

```javascript
{
  select: ['*'],
  from: 'users',
  // Criteria
  where: {
    name: 'bob'
  }
}
```

#### Modifiers

Modifiers modify the records that will be returned. This is useful when you want an ordered set of data or to limit the number of matching records returned. The supported modifiers are `limit`, `offset`, and `orderBy`.

* Limit will specify the maximum number of records you would like returned. It will prevent more records than needed from being returned in a query. The value used for `limit` must always be a positive integer.

```javascript
{
  select: ['*'],
  from: 'users',
  limit: 10
}
```

* Offset will specify where the returned results should start. It is useful for implementing paged results and is typically used with `limit` to create paginated result sets. The value used for `offset` must always be a positive integer.

```javascript
{
  select: ['*'],
  from: 'users',
  // Page 2 or the result set with 10 results per "page"
  limit: 10,
  skip: 10
}
```

* OrderBy will specify the order of the records being returned from the query. It is represented by an array of sorting conditions where each condition represents a field to sort by and a direction to use for the sorting. A condition is defined using a dictionary with a single key whose value is a direction. A direction may be either `asc` or `desc`.

```javascript
{
  select: ['*'],
  from: 'users',
  // Order by will be processed in order, so first order by age from highest to
  // lowest, then order by highScore from lowest to highest
  orderBy: [
    {
      age: 'desc'
    },
    {
      highScore: 'asc'
    }
  ]
}
```
