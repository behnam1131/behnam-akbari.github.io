---
title: TS
---


# TypeScript


## All
```csharp
    var allReady = users.All(u => u.IsReady);
```
```js
    const allReady = users.every(u => u.isReady);
```

## Any
```csharp
    var isDirty = users.Any(u => u.IsDirty);
```
```js
    const isDirty = users.some(u => u.isDirty);
```

## Average
```csharp
    var avgAge = users.Average(u => u.Age);
```
```js
    if (users.length < 1) {
        throw new Error('source contains no elements');
    }
    const avgAge = users.reduce((a, u) => a + u.age, 0) / users.length;
```

## Aggregate
```csharp
    var leftToRight = users.Aggregate(initialValue, (a, u) => /* ... */);
```
```js
    const leftToRight = users.reduce((a, u) => /* ... */, initialValue);
    const rightToLeft = users.reduceRight((a, u) => /* ... */, initialValue);
```
