---
title: TS
---


# TypeScript

## Aggregate

```csharp
{
    var leftToRight = users.Aggregate(initialValue, (a, u) => /* ... */);
}
```
```js
{
    const leftToRight = users.reduce((a, u) => /* ... */, initialValue);
    const rightToLeft = users.reduceRight((a, u) => /* ... */, initialValue);
}
```

