---
title: TS
---


# TypeScript



## Max

##### C#
```csharp
var oldestAge = users.Max(u => u.Age);
```
##### TS
```js
if (users.length < 1) {
  throw new Error('source contains no elements');
}
const oldestAge = users.reduce((oa, u) => Math.max(oa, u.age), 0);
```


## Concat

##### C#
```csharp
    var allUsers = users.Concat(moreUsers);
```
##### TS
```js
    const allUsers = [ ...users, ...moreUsers ];
```
## Sort

##### C#
```csharp
    var sorted = users.OrderBy(u => u.Age).ThenBy(u => u.Name);
```
##### TS
```js
    const sorted = users.sort((a, b) => {
    const ageDiff = b.age - a.age;
    if (ageDiff) 
        return ageDiff;
    return a.name.localeCompare(b.name); 
});
```



## Contains

##### C#
```csharp
    var hasAdmin = users.Contains(admin);
```
##### TS
```js
    const hasAdmin = users.includes(admin);
```

## All

##### C#
```csharp
    var allReady = users.All(u => u.IsReady);
```
##### TS
```js
    const allReady = users.every(u => u.isReady);
```

## Any

##### C#
```csharp
    var isDirty = users.Any(u => u.IsDirty);
```
##### TS
```js
    const isDirty = users.some(u => u.isDirty);
```

## Average

##### C#
```csharp
    var avgAge = users.Average(u => u.Age);
```
##### TS
```js
    if (users.length < 1) {
        throw new Error('source contains no elements');
    }
    const avgAge = users.reduce((a, u) => a + u.age, 0) / users.length;
```

## Sum

##### C#
```csharp
   var totalYears = users.Sum(u => u.Age);
```
##### TS
```js
    if (users.length < 1) {
    throw new Error('source contains no elements');
    }
    const totalYears = users.reduce((ty, u) => ty + u, 0);
```

## Distinct

##### C#
```csharp
    var uniqueNames = users.Select(u => u.Name).Distinct();
```
##### TS
```js
const uniqueNames = users.filter((v, i, a) => a.findIndex(t => (t.id === v.id)) === i);   
```

## Aggregate

##### C#
```csharp
    var leftToRight = users.Aggregate(initialValue, (a, u) => /* ... */);
```
##### TS
```js
    const leftToRight = users.reduce((a, u) => /* ... */, initialValue);
    const rightToLeft = users.reduceRight((a, u) => /* ... */, initialValue);
```

## groupBy

##### C#
```csharp
    var allUsers = users.Concat(moreUsers);
```
##### TS
```js
     let group = data.reduce((previous, current) => {
        if (!previous[current['title']]) {
          previous[current['title']] = [current];
        } else {
          previous[current['title']].push(current);
        }
        return previous;
      }, {});

      groupData = Object.keys(group).map(key => ({ key, value: group[key] }));
```