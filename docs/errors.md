# Errors

In the "Queryable" interface layer, raw errors returned from sending native queries can be parsed using `parseNativeQueryError()`.  The output is one of a set of standardized **error footprints**:

| Footprint             | Potential Source Queries | Error Description
|-----------------------|--------------------------|:-----------------------------------------------------------------------------------|
| notUnique             | `update`, `insert`       | The query failed because it would violate one or more uniqueness constraints.
| catchall              | _any_                    | The error from the query cannot be identified as any other known kind of query footprint.


#### notUnique

The query failed because it would violate one or more uniqueness constraints.

> _Can occur with "insert" and "update" query types._

```js
{
  identity: 'notUnique',
  keys: [ 'email_address', 'PRIMARY' ]
}
```

| Property              | Type             | Details
|-----------------------|------------------|:----------------------------------------------------------------------------------------------------------|
| identity              | ((string))       | Uniquely identifies the footprint.
| keys                  | ((array))        | An array of the names of keys where uniqueness constraint violations occurred.  Oftentimes this is a list of column names, but depending on the database keys might have custom names or be specified by a special identifier like `'PRIMARY'` (e.g. MySQL).

> **Important:**
> The `keys` array is not guaranteed to contain _all_ of the constraints which were violated.
> For example, even if `keys` is `['PRIMARY']`, there might be other keys with constraint
> violations which would be violated by the query as well.


#### catchall

The error from the query cannot be identified as any other known kind of query footprint.

> _Can occur with any type of query._

```js
{
  identity: 'catchall'
}
```

| Property              | Type             | Details
|-----------------------|------------------|:----------------------------------------------------------------------------------------------------------|
| identity              | ((string))       | Uniquely identifies the footprint.




