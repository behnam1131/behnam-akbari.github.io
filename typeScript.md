---
title: TS
---


# TypeScript


## Concat
```csharp
    var allUsers = users.Concat(moreUsers);
```
```js
    const allUsers = [ ...users, ...moreUsers ];
```


## Contains
```csharp
    var hasAdmin = users.Contains(admin);
```
```js
    const hasAdmin = users.includes(admin);
```

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

## Distinct
```csharp
    var uniqueNames = users.Select(u => u.Name).Distinct();
```
```js
    const uniqueNames = Object.keys(
        users.map(u => u.name).reduce(
            (un, u) => ({ ...un, n }),
            {}
        )
    );
```

## Aggregate
```csharp
    var leftToRight = users.Aggregate(initialValue, (a, u) => /* ... */);
```
```js
    const leftToRight = users.reduce((a, u) => /* ... */, initialValue);
    const rightToLeft = users.reduceRight((a, u) => /* ... */, initialValue);
```
