---
title: TS
---


# TypeScript

## Aggregate

```Cs
{
    var leftToRight = users.Aggregate(initialValue, (a, u) => /* ... */);
}
```
```TS
{
    const leftToRight = users.reduce((a, u) => /* ... */, initialValue);
    const rightToLeft = users.reduceRight((a, u) => /* ... */, initialValue);
}
```

