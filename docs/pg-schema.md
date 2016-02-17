## PostgreSQL Schema (Extension)

PostgreSQL supports the concept of a `schema`. To set use this in your Waterline query you can use the `opts` key.

```javascript
{
  select: ['*'],
  from: 'user',
  opts: {
    schema: 'foo'
  }
}
```
