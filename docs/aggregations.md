## Aggregations

> NOTE: this is a placeholder as I am still working though the exact interface for aggregations

#### Count

Performs a count on the specified attribute.

```javascript
{
  count: [
    'active'
  ],
  from: 'users'
}
```

#### Min

Gets the minimum value for the specified attribute.

```javascript
{
  min: [
    'age'
  ],
  from: 'users'
}
```

#### Max

Gets the maximum value for the specified attribute.

```javascript
{
  max: [
    'age'
  ],
  from: 'users'
}
```

## Sum

Retrieve the sum of the values of a given attribute.

```javascript
{
  sum: [
    'products'
  ],
  from: 'users'
}
```

## Avg

Retrieve the average of the values of a given attribute.

```javascript
{
  avg: [
    'age'
  ],
  from: 'users'
}
```
