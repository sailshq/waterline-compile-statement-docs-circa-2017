# Query Results
In the "Queryable" interface layer, raw results returned from sending native queries can be parsed using `parseNativeQueryResult()`. The normalized result depends on the query type:


| Source Query          | Result Type        |
|:----------------------|--------------------|
| insert                | ((dictionary))     |
| select                | ((array))          |
| update                | ((dictionary))     |
| delete                | ((dictionary))     |
| count                 | ((number))         |
| sum                   | ((number))         |
| avg                   | ((number))         |


#### insert

The successful result data from a query that inserted a new record.


```js
{
  inserted: '*'
}
```


| Property              | Type             | Details
|-----------------------|------------------|:----------------------------------------------------------------------------------------------------------|
| `inserted`            | ((json))         | The primary key value of the newly inserted record.  It is either a number or a string.



#### select

The successful result data from a query that fetched, joined, or aggregated a set of existing records.

```js
[
  {}
]
```

Each item in the result array is a dictionary (`{}`) that corresponds with an individual record returned from the database.  Guaranteed to be JSON-compatible (Date instances will be cast to tz-agnostic ISO 6801, aka JSON timestamp, strings).




#### update

The successful result data from a query that updated a set of existing records.


```js
{
  numRecordsUpdated: 7
}
```


| Property              | Type             | Details
|-----------------------|------------------|:-----------------------------------------------------------------------|
| `numRecordsUpdated`   | ((number))       | The number of records that were updated by this query.



#### delete

The successful result data from a query that deleted a set of existing records.


```js
{
  numRecordsDeleted: 13
}
```



| Property              | Type             | Details
|-----------------------|------------------|:-----------------------------------------------------------------------|
| `numRecordsDeleted`   | ((number))       | The number of records that were deleted by this query.




#### count

The successful result data from a query that counted a set of records.


```js
499
```

The number of records counted by this query.





#### sum

The successful result data from a query that calculated the sum over a particular field in a set of records.


```js
-939248248.4
```

The total sum aggregated by this query.



#### avg

The successful result data from a query that calculated the average (mean) over a particular field in a set of records.


```js
32.299
```

The average (mean) calculated by this query.

