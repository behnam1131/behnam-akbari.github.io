---
title: JavaScript
---


## Equal

```
    https://dorey.github.io/JavaScript-Equality-Table/
```

## defined Array

```js
new Array(0);     =>    []
new Array(0,1)    =>    [0,1]
```

## sleep

```js
export const sleep = ms =>
  new Promise(resolve => {
    setTimeout(() => {
      resolve();
    }, ms);
  });

```