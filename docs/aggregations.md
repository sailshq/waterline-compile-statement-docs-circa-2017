## Aggregations


#### Count

Counts the number of records in the table.  If a `where` clause is specified, only records which match will be counted.

```javascript
{
  count: true,
  from: 'users',
  where: {
    is_active: true
  }
}
```


## Sum

Determines the [sum](https://en.wikipedia.org/wiki/Summation) of the specified numeric field across all records in the table; or if a `where` clause is specified, only across matching records.

> The specified field should contain only numbers.  In most databases, `null`/`undefined` values will be ignored for the purpose of this calculation (i.e. counted as `0`).

```javascript
{
  sum: 'products',
  from: 'users',
  where: {
    is_active: true
  }
}
```

## Avg

Determines the [average](https://en.wikipedia.org/wiki/Arithmetic_mean) of the specified numeric field across all records in the table; or if a `where` clause is specified, only across matching records.

> The specified field should contain only numbers.  In most databases, `null`/`undefined` values will simply be excluded from the calculation.


```javascript
{
  avg: 'age',
  from: 'users',
  where: {
    is_active: true
  }
}
```
